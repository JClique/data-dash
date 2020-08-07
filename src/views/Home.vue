<template>
  <div>
  <div class="home">
    <div class="box" v-if="this.chartData.length > 0">
      <BarChart :chartData="chartData" :chartWidth="chartWidth" :chartHeight="chartHeight" />
    </div>

    <ButtonBox @randomiseData="randomiseData" title="Clean Horizontal Bar" :chartData="chartData"/>

    <div class="box" v-if="this.chartData.length > 0">
      <p>The first chart in this project was a simple horizontal bar. Each bar consists of an SVG <i>'&lt;rect&gt;'</i> element,
        and an accompanying <i>'&lt;text&gt;'</i> element confirming the value.</p>
      <p>The width of each bar is calculated as a percentage of the maximum value in the dataset, which is used as the 100% point.
        This percentage is applied to the width of the chart, which is also a variable, to calculate to length of the bar. </p>
    </div>
  </div>

  <div class="home" v-if="this.chartData.length > 0">
    <div class="box">
      <LineChart :chartData="chartData" :chartWidth="chartWidth" :chartHeight="chartHeight" />
    </div>

    <ButtonBox @randomiseData="randomiseData" title="Clean Line Area" :chartData="chartData"/>

    <div class="box">
      <p>The second chart in this project is a line-area, using a multi-sided polygon where each value is represented by a point in the shape.</p>
      <p>To create this we use a Vue JS method to calculate each plots x-axis based on the maximum value of the dataset, and the y-axis based on the length of the dataset.
        These two values are then stitched together to create a list of plots going from bottom left, up and across our peaks and valleys, then down to the bottom right.</p>
    </div>
  </div>

  <div class="home" v-if="this.chartData.length > 0">
    <div class="box">
      <BarChart :chartData="chartData" :chartLines="chartLines" :chartWidth="chartWidth" :chartHeight="chartHeight" />
    </div>

    <ButtonBox @randomiseData="randomiseData" title="Horizontal Bar ( with axis )" :chartData="chartData"/>

    <div class="box">
      <p>Axis and gridlines are created using the <i>'&lt;line&gt;'</i> element and our dynamic Chart Height and Chart Width variables.</p>
      <p>By re-using the same chart component from above, we can provide these gridlines and axis as an optional extra.</p>
      <button type="button" name="button" @click="toggleChartLines">
        Toggle Axis
      </button>
    </div>
  </div>

  </div>
</template>

<script>
import BarChart from '@/components/graph/BarChart.vue'
import LineChart from '@/components/graph/LineChart.vue'
import ButtonBox from '@/components/ButtonBox.vue'

export default {
  name: 'Home',
  components: {
    BarChart,
    LineChart,
    ButtonBox
  },
  data () {
    return {
      chartData: [],
      chartWidth: 0,
      chartHeight: 470,
      chartLines: true,
    }
  },
  created() {
    window.addEventListener('resize', this.handleResize);
    this.handleResize();
  },
  destroyed() {
    window.removeEventListener('resize', this.handleResize);
  },
  mounted() {
    this.randomiseData();
  },
  methods: {
    handleResize() {
      if (window.innerWidth <= 900) {
        this.chartWidth = window.innerWidth * 0.8;
      } else {
        this.chartWidth = 900
      }
    },
    randomiseData() {
      let length = 12;
      this.chartData = [];
      while (length > 0) {
        this.chartData.push(Math.floor(Math.random() * 100))
        length -= 1
      }
    },
    toggleChartLines() {
      this.chartLines = !this.chartLines
    }
  }
}
</script>


<style scoped>
.home {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}

.box {
  flex: 1 1 400px;
  background-color: #f2f2f2;
  padding: 1rem;
  margin: 1rem;
  border-radius: 10px;
}

.box p {
  padding: 1rem;
  text-align: justify;
}

.box button {
  background-color: white;
  padding: .5rem 1rem;
  outline: 2px dashed var(--lavender);
  outline-offset: 2px;
  border: none;
  appearance: none;
  font-family: 'Ubuntu Mono', monospace;
  font-size: 1rem;
  float: right;
}

.box button:hover {
  background-color: var(--lavender);
}

.box button:active {
  background-color: var(--cyan);
}

</style>
