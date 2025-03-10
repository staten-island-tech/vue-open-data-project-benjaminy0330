<script setup>
//header of website
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'



</script>

<template>
  <header>
    
    <div class="wrapper">
      <HelloWorld msg="You did it!" />

        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/brooklyn">Brooklyn</RouterLink>
        <RouterLink to ="/bronx"> Bronx</RouterLink>
      
    </div>
  </header>
   <DogBite />
  <RouterView />

</template>


<style scoped>
.nav {
  text-align: center;
  color: blue;
}
</style>
