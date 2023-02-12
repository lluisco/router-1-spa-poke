<script setup>

import axios from 'axios'
import {ref} from 'vue'
import PokemonItem from '../components/PokemonItem.vue'
import {useGetData} from '@/composables/getData'

const pokemons = ref([])

const {data, loading, error, getData} = useGetData() 

getData("https://pokeapi.co/api/v2/pokemon")

</script>

<template>
    <h1>Pokemons</h1>
    <p v-if="loading">Cargando info...</p>
    <div class="alert alert-danger mt-2" v-if="error">{{ error }}</div>
    <div v-if="data">
        <PokemonItem class="mt-2" v-for="(pokemon, index) in data.results" :key="index" :name="pokemon.name"></PokemonItem>
        <div class="mt-2">
            <button :disabled="!data.previous" class="btn btn-success me-2" @click="getData(data.previous)">Previous</button>
            <button :disabled="!data.next" class="btn btn-primary" @click="getData(data.next)">Next</button>
        </div>
    </div>
    
</template>