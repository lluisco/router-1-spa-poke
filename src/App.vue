<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <nav class="navbar navbar-dark bg-dark">
    <router-link class="navbar-brand" to="/">
      <img src="@/assets/logo.svg" width="30" height="30" class="d-inline-block align-top" alt="">
      PokeAPI
    </router-link>
    <div>
      <router-link class="btn btn-outline-primary me-2" to="/">Home</router-link>
      <router-link class="btn btn-outline-primary" to="pokemons">Pokemons</router-link>

    </div>
</nav>
  
  <div class="container text-center">
    <RouterView />
  </div>
  
</template>

<style scoped>

</style>
