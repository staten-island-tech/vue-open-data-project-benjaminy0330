<template>
  <div>
    <Pie v-if="chartData" :data="chartData" :options="chartOptions"  class = "pie"/>
    <p v-else>Loading data...</p>
  </div>
</template>


<script setup>
import { ref, onMounted } from 'vue';
import { Pie } from 'vue-chartjs';
import { Chart as ChartJS, Title, Tooltip, Legend, ArcElement, CategoryScale, LinearScale } from 'chart.js';


ChartJS.register(Title, Tooltip, Legend, ArcElement, CategoryScale, LinearScale);


const chartData = ref(null);
const chartOptions = ref({
  responsive: true,
  plugins: {
    legend: {
      position: 'top',
    },
    title: {
      display: true,
      text: 'Distribution of Dog Breeds in NYC',
    },
  },
});


onMounted(async () => {
  try {
  
    const response = await fetch('https://data.cityofnewyork.us/resource/rsgh-akpg.json?$limit=70');
    const dogs = await response.json();

    const breedCounts = dogs.reduce((acc, dog) => {
      const breed = dog.breed;
      if (breed) {
        acc[breed] = (acc[breed] || 0) + 1;
      }
      return acc;
    }, {});

    const breeds = Object.keys(breedCounts);
    const breedData = breeds.map(breed => breedCounts[breed]);

   
    chartData.value = {
      labels: breeds,
      datasets: [
        {
          label: 'Dog Breeds',
          data: breedData,
          backgroundColor: breeds.map(() => `#${Math.floor(Math.random()*16777215).toString(16)}`), 
        },
      ],
    };
  } catch (error) {
    console.error('Error fetching or processing data:', error);
  }
});
</script>
