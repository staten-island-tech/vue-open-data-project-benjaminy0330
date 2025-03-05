<template>
  <div>
    <TheWelcome />
    <TheDogBite v-for = "dogbite in dogbites" :key = data.uniqueid />
  </div>
</template>

<script setup>
import TheWelcome from '@/components/TheWelcome.vue';
import TheDogBite from '@/components/TheDogBite.vue';
</script>

<style scoped>

</style>