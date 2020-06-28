<script>
import { Bar } from "vue-chartjs";
export default {
  extends: Bar,
  props: {
    chartData: Object
  },
  data() {
    return {
      options: {
        responsive: true,
        maintainAspectRatio: false,
        legend: {
          display: false
        }
      }
    };
  },
  mounted() {
    this.renderChart(this.chartData, this.options);
  }
};
</script>
