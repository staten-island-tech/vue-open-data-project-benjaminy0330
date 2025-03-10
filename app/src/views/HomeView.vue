<template>
  <div>
    <TheWelcome />
    <TheDogBite v-for = "data in data" :key = data.uniqueid  />
  </div>
</template>

<script setup>
import TheWelcome from '@/components/TheWelcome.vue';
import TheDogBite from '@/components/DogBite.vue';


</script>

<style scoped>

</style>