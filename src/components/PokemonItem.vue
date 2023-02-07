<script setup>
import {RouterLink} from 'vue-router'

defineProps(['name','link'])
</script>

<template>
    <div>
        <router-link :to="`/pokemons/${name}`">{{ name }}</router-link>
    </div>
</template>