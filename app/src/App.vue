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
        <RouterLink to="/brooklyn">brooklyn</RouterLink>
        <RouterLink to ="/bronx"> bronx</RouterLink>
      
    </div>
  </header>
    <h1>home page will hold sdasdapi</h1>
  <RouterView />
</template>

<style scoped>
.nav {
  text-align: center;
}
</style>
