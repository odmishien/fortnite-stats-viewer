<template>
  <b-container fluid>
    <h2>Fortnite-stats-viewer</h2>
    <b-form-group label="EpicアカウントID" label-for="account-id">
      <p class="text-muted">EpicアカウントIDは<a href="https://www.epicgames.com/account/personal?productName=epicgames&lang=ja">ここ</a>から確認できます</p>
      <b-form-input id="account-id" v-model="accountID" placeholder></b-form-input>
    </b-form-group>
    <b-button @click="getGlobalStats(accountID)" variant="success">通算成績を見る</b-button>
    <Result :result="result" v-if="result"/>
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
      result: null
    };
  },
  methods: {
    getGlobalStats(id) {
      axios
        .get("https://fortnite-stats-viewer-api.herokuapp.com/global-stats", {
          params: {
            account_id: id
          }
        })
        .then(res => {
          this.result = res.data;
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
