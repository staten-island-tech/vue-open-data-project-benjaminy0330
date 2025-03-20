<template>
    <div class = "info">
    
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
})

</script>

<style scoped>

</style>