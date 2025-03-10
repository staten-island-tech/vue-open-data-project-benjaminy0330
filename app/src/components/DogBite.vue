<template>
    <div class = "info">
      <h1></h1>
    </div>
</template>

<script setup>
const URL = "https://data.cityofnewyork.us/resource/rsgh-akpg.json";
async function fetchData(URL) {
  try {
    const response = await fetch(URL);
    const data = await response.json();
   
    console.log(data);
  } catch (err) {
    console.error(err);
  }
}
fetchData(URL);


</script>

<style scoped>

</style>