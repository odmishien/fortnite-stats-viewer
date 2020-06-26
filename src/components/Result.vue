
<template>
  <b-container align-h="center">
    <b-row class="my-5">
      <b-col cols="12">
        <h1>ユーザー名: {{userName}} (Lv.{{level}})</h1>
      </b-col>
    </b-row>
    <hr>
    <b-row class="my-5">
      <b-col cols="12">
        <h2>ソロ通算</h2>
      </b-col>
      <b-col cols="4">
        <h4>キル数</h4>
        <br />
        <h2>{{resultSolo.kills}}</h2>
      </b-col>
      <b-col cols="4">
        <h4>試合数</h4>
        <br />
        <h2>{{resultSolo.matchesplayed}}</h2>
      </b-col>
      <b-col cols="4">
        <h4>キルレート</h4>
        <br />
        <h2>{{resultSolo.kd}} kill/match</h2>
      </b-col>
    </b-row>

    <b-row class="my-3">
      <b-col cols="12">
        <h4>プレイ時間</h4>
        <br />
        <h2>{{resultSolo.minutesplayed / 60}} 時間</h2>
      </b-col>
    </b-row>

    <b-row class="my-3">
      <b-col cols="6">
        <h4>ビクロ</h4>
        <br />
        <h2>{{resultSolo.placetop1}} 回</h2>
      </b-col>
      <b-col cols="6">
        <h4>ビクロレート</h4>
        <br />
        <h2>{{resultSolo.winrate}}</h2>
      </b-col>
    </b-row>
    <hr>
    <b-row class="my-5">
      <b-col cols="12">
        <h2>デュオ通算</h2>
      </b-col>
      <b-col cols="4">
        <h4>キル数</h4>
        <br />
        <h2>{{resultDuo.kills}}</h2>
      </b-col>
      <b-col cols="4">
        <h4>試合数</h4>
        <br />
        <h2>{{resultDuo.matchesplayed}}</h2>
      </b-col>
      <b-col cols="4">
        <h4>キルレート</h4>
        <br />
        <h2>{{resultDuo.kd}} kill/match</h2>
      </b-col>
    </b-row>

    <b-row class="my-3">
      <b-col cols="12">
        <h4>プレイ時間</h4>
        <br />
        <h2>{{resultDuo.minutesplayed / 60}} 時間</h2>
      </b-col>
    </b-row>

    <b-row class="my-3">
      <b-col cols="6">
        <h4>ビクロ</h4>
        <br />
        <h2>{{resultDuo.placetop1}} 回</h2>
      </b-col>
      <b-col cols="6">
        <h4>ビクロレート</h4>
        <br />
        <h2>{{resultDuo.winrate}}</h2>
      </b-col>
    </b-row>
    <hr>
    <b-row class="my-5">
      <b-col cols="12">
        <h2>スクワッド通算</h2>
      </b-col>
      <b-col cols="4">
        <h4>キル数</h4>
        <br />
        <h2>{{resultSquad.kills}}</h2>
      </b-col>
      <b-col cols="4">
        <h4>試合数</h4>
        <br />
        <h2>{{resultSquad.matchesplayed}}</h2>
      </b-col>
      <b-col cols="4">
        <h4>キルレート</h4>
        <br />
        <h2>{{resultSquad.kd}} kill/match</h2>
      </b-col>
    </b-row>

    <b-row class="my-3">
      <b-col cols="12">
        <h4>プレイ時間</h4>
        <br />
        <h2>{{resultSquad.minutesplayed / 60}} 時間</h2>
      </b-col>
    </b-row>

    <b-row class="my-3">
      <b-col cols="6">
        <h4>ビクロ</h4>
        <br />
        <h2>{{resultSquad.placetop1}} 回</h2>
      </b-col>
      <b-col cols="6">
        <h4>ビクロレート</h4>
        <br />
        <h2>{{resultSquad.winrate}}</h2>
      </b-col>
    </b-row>
  </b-container>
</template>
<script>
export default {
  name: "Result",
  props: {
    result: Object
  },
  data() {
    return {
      userName: this.result.name,
      level: this.result.account.level,
      resultSolo: this.result.global_stats.solo,
      resultDuo: this.result.global_stats.duo,
      resultSquad: this.result.global_stats.squad
    };
  }
};
</script>
