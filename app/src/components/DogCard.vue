<template>
    <div class="dog-card">
      <h2>Dog ID: {{ dog.uniqueid }}</h2>
      <h3>Gender:{{ dog.gender }}</h3>
      <h3>Breed: {{ dog.breed }}</h3>
      <h3>Date: {{ dog.dateofbite }}</h3>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      dog: Object
    }
  };
  </script>
  
  <style scoped>
  .dog-card {
    border: 1px solid #050505;
    border-radius: 8px;
    padding: 16px;
    margin: 8px;
    box-shadow: 2px 2px 12px rgba(0, 0, 0, 0.1);
    width: 20rem;
  }
  </style>
  