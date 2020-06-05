<template>
  <div class="container">
    <div>
      <LineChart :chart-data="chartData" :options="chartOptions" />
      <button @click="addData">Add Data</button>
    </div>
  </div>
</template>

<script>
import LineChart from '@/components/LineChart.vue'
export default {
  components: { LineChart },
  data: () => ({
    chartData: {
      datasets: [
        {
          data: [0.12, 0.1, 0.05],
          fill: false
        }
      ],
      labels: ['0', '50K', '100K', '150K', '200K']
    },
    chartOptions: {
      scales: {
        yAxes: [
          {
            ticks: {
              beginAtZero: true
            }
          }
        ]
      }
    }
  }),
  methods: {
    addData() {
      const newData = this.chartData.datasets[0].data
      newData.push(newData[newData.length - 1] - 0.2)

      this.chartData = {
        ...this.chartData,
        datasets: [
          {
            data: newData,
            fill: false
          }
        ]
      }
    }
  }
}
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
