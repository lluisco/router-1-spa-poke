<script setup>
import axios from 'axios'
import {ref} from 'vue'
import {useRoute, useRouter} from "vue-router";

const pokemon = ref({})
const route = useRoute();
const router = useRouter();

const back = () => {
    router.push('/pokemons')
}


const getData = async () => {
    try {
        const { data } = await axios('https://pokeapi.co/api/v2/pokemon/' + route.params.name)
        pokemon.value = data
    } catch (error) {
        console.log(error)
        pokemon.value = null;
    }
}

getData()

</script>

<template>
    <div v-if="pokemon">
        <img :src="pokemon.sprites?.front_default" alt="">
        <h1>Poke name: {{ $route.params.name }}</h1>
    </div>
    <div v-else>
        <h1>No existe el pokemon</h1>
    </div>
    <button @click="back" class="btn btn-outline-primary">Back</button>
</template>