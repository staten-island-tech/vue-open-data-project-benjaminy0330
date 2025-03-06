<template>
  <div>
    <TheWelcome />
    <TheDogBite v-for = "data in data" :key = data.uniqueid  />
  </div>
</template>

<script setup>
import TheWelcome from '@/components/TheWelcome.vue';
import TheDogBite from '@/components/TheDogBite.vue';


</script>

<style scoped>

</style>