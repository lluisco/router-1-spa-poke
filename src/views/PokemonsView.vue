<script setup>

import axios from 'axios'
import {ref} from 'vue'

import PokemonItem from '../components/PokemonItem.vue'

const pokemons = ref([])

const getData = async () => {
    try {
        const { data } = await axios('https://pokeapi.co/api/v2/pokemon/')
        pokemons.value = data.results
    } catch (error) {
        console.log(error)
    }
}

getData()

</script>

<template>
    <h1>Pokemons</h1>
    
    <PokemonItem v-for="(pokemon, index) in pokemons" :key="index" :name="pokemon.name"></PokemonItem>
    
</template>