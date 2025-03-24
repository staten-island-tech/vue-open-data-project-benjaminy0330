<template>
    <div class = "info">
      <h2>{{ data.uniqueid }}</h2>
      <h2>{{ data.dateofbite }}</h2>
      <h2>{{ data.borough}}</h2>
      <h2>{{ data.sprayneutral}}</h2>
    </div>
</template>

<script setup>

const URL = "https://data.cityofnewyork.us/resource/rsgh-akpg.json";
import {ref, onMounted} from 'vue';
async function fetchData(URL) {
  try {
    const response = await fetch(URL);
    const data = await response.json();
   
    console.log(data)
  } catch (err) {
    console.error(err);
  }
}
onMounted(() =>{
 fetchData(URL);
});

</script>

<style scoped>

</style>