<script setup>
import {ref} from 'vue'
import {useRoute, useRouter} from "vue-router";
import {useGetData} from "@/composables/getData"

const pokemon = ref({})
const route = useRoute();
const router = useRouter();
const {data, loading, error, getData} = useGetData() 

const back = () => {
    router.push('/pokemons')
}

getData('https://pokeapi.co/api/v2/pokemon/' + route.params.name)

</script>

<template>
    <p v-if="loading">Cargando información...</p>
    <div class="alert alert-danger mt-2" v-if="error">{{ error }}</div>
    <div v-if="data">
        <div v-if="pokemon">
            <img :src="data.sprites?.front_default" alt="">
            <h1>Poke name: {{ $route.params.name }}</h1>
        </div>
    </div>
    <button @click="back" class="btn btn-outline-primary">Back</button>
</template>