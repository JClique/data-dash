<template>
  <div>
  <div class="home">
    <h2 v-if="this.chartData.length > 0">Clean Horizontal Bar</h2>

    <div class="box" v-if="this.chartData.length > 0">
      <BarChart :chartData="chartData" :chartWidth="chartWidth" :chartHeight="chartHeight" />
    </div>

    <div class="box btn-box">
      <div class="box-content">
        <p>Generate some randomised data to see chart transitions and animations.</p>
        <button type="button" name="button" @click="randomiseData">
          Shuffle Data
        </button>
      </div>
    </div>

    <div class="box" v-if="this.chartData.length > 0">
      <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.</p>
    </div>
  </div>


  <div class="home">
    <h2 v-if="this.chartData.length > 0">Clean Line Area</h2>

    <div class="box" v-if="this.chartData.length > 0">
      <LineChart :chartData="chartData" :chartWidth="chartWidth" :chartHeight="chartHeight" />
    </div>


    <div class="box btn-box" v-if="this.chartData.length > 0">
      <div class="box-content">
        <p>Generate some randomised data to see chart transitions and animations.</p>
        <button type="button" name="button" @click="randomiseData">
          Shuffle Data
        </button>
      </div>
    </div>

    <div class="box" v-if="this.chartData.length > 0">
      <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.</p>
    </div>
  </div>
  </div>
</template>

<script>
import BarChart from '@/components/graph/BarChart.vue'
import LineChart from '@/components/graph/LineChart.vue'

export default {
  name: 'Home',
  components: {
    BarChart,
    LineChart
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

.box.btn-box {
  display: flex;
  align-items: center;
  justify-content: center;
}

.box-content {
  text-align: center;
}

.box.btn-box p {
  padding: 1rem;
}
</style>
