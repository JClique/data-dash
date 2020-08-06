<template>
  <div>
  <div class="home">
    <div class="box" v-if="this.chartData.length > 0">
      <BarChart :chartData="chartData" :chartWidth="chartWidth" :chartHeight="chartHeight" />
    </div>

    <ButtonBox @randomiseData="randomiseData" title="Clean Horizontal Bar"/>

    <div class="box" v-if="this.chartData.length > 0">
      <p>The first chart in this project was a simple horizontal bar. Each bar consists of an SVG <i>'&lt;rect&gt;'</i> element,
        and an accompanying <i>'&lt;text&gt;'</i> element confirming the value.</p>
      <p>This text follows the end of the bar in a smooth animation when data is loaded or changed, and each bar changes on mouseover to improve use experience.
        The width of the chart spans the max value in the dataset for consistency.</p>
    </div>
  </div>

  <div class="home" v-if="this.chartData.length > 0">
    <div class="box">
      <LineChart :chartData="chartData" :chartWidth="chartWidth" :chartHeight="chartHeight" />
    </div>

    <ButtonBox @randomiseData="randomiseData" title="Clean Line Area" />

    <div class="box">
      <p>The second chart in this project is a line-area, using a multi-sided polygon where each value is represented by a point in the shape.</p>
      <p>To create this we use a Vue JS method to calculate each plots x-axis based on the maximum value of the dataset, and the y-axis based on the length of the dataset.
        These two values are then stitched together to create a list of plots going from bottom left, up and across our peaks and valleys, then down to the bottom right.</p>
    </div>
  </div>

  <div class="home" v-if="this.chartData.length > 0">
    <div class="box">
      <BarChart :chartData="chartData" :chartLines="true" :chartWidth="chartWidth" :chartHeight="chartHeight" />
    </div>

    <ButtonBox @randomiseData="randomiseData" title="Horizontal Bar ( with axis )"/>

    <div class="box">
      <p>Now that we have two types of graph, it's time to add some axis. These are created using the <i>'&lt;line&gt;'</i> element and our dynamic Chart Heigh and Chart Width variables. </p>
      <p>As with our previous chart, each bar changes on mouseover and our gridlines rect in a similar manor.</p>
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


</style>
