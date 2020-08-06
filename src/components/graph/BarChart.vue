<template lang="html">
  <div class="bar">
    <svg :width="chartWidth + 20" :height="chartHeight + 20">

      <g v-if="this.chartLines">
        <line :x1="10" :x2="chartWidth + 10" :y1="chartHeight + 10" :y2="chartHeight + 10"></line>
        <line :x1="11" :x2="11" :y1="0" :y2="chartHeight + 10"></line>

        <line class="marker" v-for="i in 10" :key="i"
          :x1="(dataSteps * i) + 9" :x2="(dataSteps * i) + 9" :y1="0" :y2="chartHeight + 9"></line>
      </g>

      <g v-for="(value, i) in animatedChartData" :key="i"
        :transform="`translate(0, ${i * 40})`">
        <rect height="30" :width="barWidth(value)" x="10"></rect>
        <text y="20" :x="barWidth(value)">{{ value | round }}</text>
      </g>
    </svg>
  </div>
</template>

<script>
export default {
  name: "BarChart",
  props: ["chartData", "chartWidth", "chartHeight", "chartLines"],
  data() {
    return {
      animatedChartData: [0,0,0,0,0,0,0,0,0,0,0,0]
    }
  },
  methods: {
    barWidth(value) {
      return this.chartWidth / this.dataMax * value;
    },
    animate() {
      const fromValues = this.animatedChartData;
      const toValues = this.chartData;

      const duration = 600;
      const start = Date.now();

      const frame = () => {
        const elapsed = Date.now() - start;
        const percent = elapsed / duration;

        if (percent >= 1) {
          this.animatedChartData = this.chartData;
        } else {
          this.animatedChartData = toValues.map((toVal, i) => {
            const fromVal = fromValues[i];
            return fromVal + (toVal - fromVal) * percent;
          });
          requestAnimationFrame(frame);
        }
      };

      requestAnimationFrame(frame);
    },
  },
  mounted() {
    this.animate();
  },
  watch: {
    chartData() {
      this.animate();
    },
  },
  computed: {
    dataMax() {
      return Math.max(...this.chartData);
    },
    dataSteps() {
      return this.chartWidth / 10;
    }
  },
  filters: {
  round(number) {
    return Math.round(number);
  },
},
}
</script>

<style scoped>

  .bar {
    padding: 0;
    padding-top: 1rem;
  }

  line {
    stroke: var(--lavender);
    stroke-width: 2;
  }

  line.marker {
    stroke-width: 1;
  }

  line.marker:hover {
    stroke: white;
    stroke-width: 3;
  }

  text {
    fill: white;
    text-anchor: end;
    font-family: 'Ubuntu Mono', monospace;
    -webkit-user-select: none;
    -moz-user-select: none;
    -ms-user-select: none;
    user-select: none;
  }

  rect {
    fill: var(--pink);
    transition-property: width;
  }

  rect:hover {
    fill: var(--d-pink);
  }

</style>
