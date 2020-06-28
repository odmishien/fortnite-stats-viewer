<template>
  <b-container fluid>
    <h2>Fortnite-stats-viewer</h2>
    <b-form-group label="EpicアカウントID" label-for="account-id">
      <p class="text-muted">
        EpicアカウントIDは
        <a
          href="https://www.epicgames.com/account/personal?productName=epicgames&lang=ja"
        >ここ</a>から確認できます
      </p>
      <b-alert :show="error.length > 0" variant="danger">{{error}}</b-alert>
      <b-form-input id="account-id" v-model="accountID" placeholder></b-form-input>
    </b-form-group>
    <b-button @click="getGlobalStats(accountID)" variant="primary">通算成績を見る</b-button>
    <Result :result="result" v-if="result" />
  </b-container>
</template>

<script>
import axios from "axios";
import Result from "./Result.vue";
export default {
  name: "Main",
  components: {
    Result
  },
  data() {
    return {
      accountID: "",
      result: null,
      error: ""
    };
  },
  methods: {
    resetResult() {
      this.result = null;
    },
    getGlobalStats(id) {
      this.resetResult();
      if (!this.accountID) {
        this.error = "IDを入力してください";
        return;
      }
      axios
        .get("https://fortnite-stats-viewer-api.herokuapp.com/global-stats", {
          params: {
            account_id: id
          }
        })
        .then(res => {
          if (!res.data.result) {
            this.error = res.data.error;
          } else {
            if (this.result) {
              this.result = Object.assign(this.result, res.data);
            } else {
              this.result = res.data;
            }
          }
        })
        .catch(err => {
          this.error = "サーバーとの通信に失敗しました";
          console.log(err);
        });
    },
    // とりあえずrecentMatchesは非対応
    getRecentMatches(id) {
      axios
        .get("https://fortnite-stats-viewer-api.herokuapp.com/recent-matches", {
          params: {
            account_id: id
          }
        })
        .then(res => {
          this.result = res.data;
        });
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
