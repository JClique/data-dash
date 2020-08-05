<template lang="html">
  <div class="bar">
    <svg :width="chartWidth" :height="chartHeight">
      <g v-for="(value, i) in chartData" :key="i"
        :transform="`translate(0, ${i * 40})`">
        <rect height="30" :width="barWidth(value)"></rect>
        <text y="21" :x="barWidth(value) - 10">{{ value }}</text>
      </g>
    </svg>
  </div>
</template>

<script>
export default {
  name: "Bar",
  props: ["chartData"],
  data () {
    return {
      chartWidth: 0,
      chartHeight: 470
    }
  },
  created() {
    window.addEventListener('resize', this.handleResize);
    this.handleResize();
  },
  destroyed() {
    window.removeEventListener('resize', this.handleResize);
  },
  methods: {
    barWidth(value) {
      return this.chartWidth / this.dataMax * value;
    },
    handleResize() {
      if (window.innerWidth <= 900) {
        this.chartWidth = window.innerWidth * 0.8;
      } else {
        this.chartWidth = 900
      }
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

  .bar {
    padding: 1rem;
    transition: .4s;
  }

  text {
    fill: white;
    text-anchor: end;
    font-family: 'Ubuntu Mono', monospace;
  }

  rect {
    fill: var(--d-pink);
  }

</style>
