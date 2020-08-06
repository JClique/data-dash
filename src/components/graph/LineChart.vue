<template lang="html">
  <div class="line">

    <svg :width="chartWidth" :height="chartHeight">
      <polygon
         :points="lineChartData(chartData)"/>
    </svg>
  </div>
</template>

<script>
export default {
  name: "LineChart",
  props: ["chartData", "chartWidth", "chartHeight"],
  methods: {
    lineChartData(chartData) {
      if (chartData.length > 1) {
        var points = "0, " + this.chartHeight + " ";
        for (var x = 0; x < chartData.length; x++) {
          var perc = chartData[x] / this.dataMax;
          var steps = (this.chartWidth / chartData.length) * 1.1;
          var point = (steps * (x)).toFixed(2) + "," + (this.chartHeight - (this.chartHeight * perc)).toFixed(2) + " ";
          points += point;
        }
      }
      points += "100, 100000";
      return points
    }
  },
  computed: {
    dataMax() {
      return Math.max(...this.chartData);
    }
  }
}
</script>

<style scoped>

  .line {
    padding: 1rem;
    transition: .4s;
  }

  polygon {
    fill: var(--d-pink);
    stroke: var(--d-pink);
    stroke-width: 3;
    transition: .6s;
  }

</style>
