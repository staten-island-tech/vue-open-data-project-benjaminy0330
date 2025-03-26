<template>
  <div>
    <header>
   
   <div class="wrapper">
     <HelloWorld />


       <RouterLink to="/">Home</RouterLink>
       <RouterLink to ="/Gender">Gender</RouterLink>
       <RouterLink to ="/Breed">Breed</RouterLink>
       
    
   </div>
 </header>
  
 <RouterView />


  </div>
</template>

<script setup>
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'

</script>

<style scoped>
.wrapper{
  text-align: center;
}
</style>






