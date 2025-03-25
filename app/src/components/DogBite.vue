<template>
  <div>
    <h2>Dog Gender Pie Chart</h2>
    <Pie :data="chartData" :options="chartOptions" />
  </div>
</template>

<script>
import { defineComponent, ref, onMounted } from 'vue'; // Import defineComponent
import { Pie } from 'vue-chartjs';
import { Chart, registerables } from 'chart.js';
Chart.register(...registerables);

export default defineComponent({
  components: { Pie },
  setup() {
    const chartData = ref({
      labels: [],
      datasets: [
        {
          label: 'Gender of Dogs',
          data: [],
          backgroundColor: ['#FF6384', '#36A2EB'],
        },
      ],
    });

    const chartOptions = ref({
      responsive: true,
      plugins: {
        legend: { position: 'top' },
      },
    });

    onMounted(async () => {
      try {
        const response = await fetch('https://data.cityofnewyork.us/resource/rsgh-akpg.json');
        const data = await response.json();

        // Example processing (grouping by gender)
        const genderCounts = { Male: 0, Female: 0 };

        data.forEach((item) => {
          const gender = item.gender || 'Unknown';
          if (gender === 'Male' || gender === 'Female') {
            genderCounts[gender]++;
          }
        });

        // Set chart data
        chartData.value.labels = Object.keys(genderCounts);
        chartData.value.datasets[0].data = Object.values(genderCounts);
      } catch (error) {
        console.error('Error fetching data:', error);
      }
    });

    return { chartData, chartOptions };
  },
});
</script>

<style scoped>
h2 {
  text-align: center;
}
</style>
