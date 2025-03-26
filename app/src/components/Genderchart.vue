<template>
  <div>
    <Bar v-if="chartData" :data="chartData" :options="chartOptions" />
    <p v-else>Loading data...</p>
  </div>
</template>


<script setup>
import { ref, onMounted } from 'vue';
import { Bar } from 'vue-chartjs';
import { Chart as ChartJS, Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale } from 'chart.js';


ChartJS.register(Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale);

const chartData = ref(null);
const chartOptions = ref({
  responsive: true,
  plugins: {
    legend: {
      position: 'top',
    },
    title: {
      display: true,
      text: 'Dog Gender Distribution (M, F, U)',
    },
  },
  scales: {
    x: {
      beginAtZero: true,
    },
  },
});


onMounted(async () => {
  try {
  
    const response = await fetch('https://data.cityofnewyork.us/resource/rsgh-akpg.json?$limit=1000');
    const dogs = await response.json();

    const genderCounts = dogs.reduce((acc, dog) => {
      const gender = dog.gender;
      if (gender === "M" || gender === "F" || gender === "U") {
        acc[gender] = (acc[gender] || 0) + 1;
      }
      return acc;
    }, {});

    const genders = ['M', 'F', 'U'];
    const genderData = genders.map(gender => genderCounts[gender] || 0);

    chartData.value = {
      labels: genders,
      datasets: [
        {
          label: 'Dog Gender Count',
          data: genderData,
          backgroundColor: ['#0CADE8', '#E80C90', '#353535'], 
        },
      ],
    };
  } catch (error) {
    console.error('Error fetching or processing data:', error);
  }
});
</script>


