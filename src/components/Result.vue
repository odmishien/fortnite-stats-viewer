
<template>
  <b-container align-h="center">
    <b-row class="my-5">
      <b-col cols="12">
        <h3>{{userName}} (Lv.{{level}})</h3>
      </b-col>
    </b-row>
    <hr />
    <b-row class="my-5">
      <b-col cols="12">
        <BarChart :chartData="killRateData" />
      </b-col>
      <b-col cols="12">
        <h4>キルレート</h4>
      </b-col>
    </b-row>
    <hr />
    <b-row class="my-5">
      <b-col cols="12">
        <BarChart :chartData="killData" />
      </b-col>
      <b-col cols="12">
        <h4>キル数</h4>
      </b-col>
    </b-row>
    <hr />
    <b-row class="my-5">
      <b-col cols="12">
        <BarChart :chartData="matchNumData" />
      </b-col>
      <b-col cols="12">
        <h4>試合数</h4>
      </b-col>
    </b-row>
    <hr />

    <b-row class="my-5">
      <b-col cols="12">
        <BarChart :chartData="placeTop1Data" />
      </b-col>
      <b-col cols="12">
        <h4>ビクロ回数</h4>
      </b-col>
    </b-row>
    <hr />

    <b-row class="my-5">
      <b-col cols="12">
        <BarChart :chartData="minutesplayedData" />
      </b-col>
      <b-col cols="12">
        <h4>プレイ時間(h)</h4>
      </b-col>
    </b-row>
  </b-container>
</template>
<script>
import BarChart from "./BarChart";
const barLabel = ["ソロ", "デュオ", "スクワッド"];
const barColor = ["#ff386f", "#fff336", "#6981ff"];
export default {
  name: "Result",
  components: {
    BarChart
  },
  props: {
    result: Object
  },
  data() {
    return {
      userName: this.result.name,
      level: this.result.account.level,
      killRateData: {
        labels: barLabel,
        datasets: [
          {
            data: [
              this.result.global_stats.solo.kd,
              this.result.global_stats.duo.kd,
              this.result.global_stats.squad.kd
            ],
            backgroundColor: barColor
          }
        ]
      },
      killData: {
        labels: barLabel,
        datasets: [
          {
            data: [
              this.result.global_stats.solo.kills,
              this.result.global_stats.duo.kills,
              this.result.global_stats.squad.kills
            ],
            backgroundColor: barColor
          }
        ]
      },
      matchNumData: {
        labels: barLabel,
        datasets: [
          {
            data: [
              this.result.global_stats.solo.matchesplayed,
              this.result.global_stats.duo.matchesplayed,
              this.result.global_stats.squad.matchesplayed
            ],
            backgroundColor: barColor
          }
        ]
      },
      placeTop1Data: {
        labels: barLabel,
        datasets: [
          {
            data: [
              this.result.global_stats.solo.placetop1,
              this.result.global_stats.duo.placetop1,
              this.result.global_stats.squad.placetop1
            ],
            backgroundColor: barColor
          }
        ]
      },
      minutesplayedData: {
        labels: barLabel,
        datasets: [
          {
            data: [
              this.result.global_stats.solo.minutesplayed / 60,
              this.result.global_stats.duo.minutesplayed / 60,
              this.result.global_stats.squad.minutesplayed / 60
            ],
            backgroundColor: barColor
          }
        ]
      },
      resultSolo: this.result.global_stats.solo,
      resultDuo: this.result.global_stats.duo,
      resultSquad: this.result.global_stats.squad
    };
  }
};
</script>
