<template>
  <div class="dog-list">
    <DogCard v-for="dog in dogfilter" :key="dog.uniqueid" :dog="dog" />
  </div>
</template>

<script setup>
import { ref, onMounted, computed } from 'vue';
import DogCard from '@/components/DogCard.vue';

const dogcards = ref([]);
const URL = `https://data.cityofnewyork.us/resource/rsgh-akpg.json?$limit=200`;

const getDogs = async () => {
  try {
    const response = await fetch(URL);
    const data = await response.json();
    dogcards.value = data; 
  } catch (error) {
    console.error("Error getting data", error);
  }
};

onMounted(getDogs);


const dogfilter = computed(() =>
  dogcards.value.filter(dog =>
    dog.uniqueid &&  
    dog.breed &&       
    dog.gender&&
    dog.dateofbite
    
  )
);
</script>

<style scoped>
.dog-list {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}
</style>
