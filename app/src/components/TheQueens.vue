
<template>
    <Bar
      id="my-chart-id"
      :options="chartOptions"
      :data="chartData"
    />

    <h2></h2>
  </template>
  
  <script>
  import DogBite from './DogBite.vue'
  import { Bar } from 'vue-chartjs'
  import { Chart as ChartJS, Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale } from 'chart.js'
  
  ChartJS.register(Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale)
  
  
  export default {
    name: 'BarChart',
    components: { Bar },
    data() {
      return {
        chartData: {
          labels: [  ],
          datasets: [ { data:"https://data.cityofnewyork.us/resource/rsgh-akpg.json" } ]
        },
        chartOptions: {
          responsive: true
        }
      }
    }
  }
  </script>