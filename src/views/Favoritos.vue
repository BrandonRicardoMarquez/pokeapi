<script setup>
import {useFavoritosStore} from '@/store/favoritos'
import { storeToRefs } from 'pinia';
import {RouterLink} from "vue-router"

const useFavoritos = useFavoritosStore()

const {favoritos} = storeToRefs(useFavoritos)
const {remove} = useFavoritos
</script>

<template>
    <div class="container bg-white">
    <h1 >Favoritos</h1>
    <h2 v-if="favoritos.length === 0" > Sin favoritos</h2>
    <ul class="list-group text-center" v-else>
        <li class="list-group-item" v-for="poke 
        in favoritos" 
        :key="poke.id">
        <div>
            {{ poke.name }}
        </div>
        <div>
            <RouterLink class="btn btn-outline-dark me-2" :to="`/pokemons/${poke.name}`" >Inf.DataPoke</RouterLink>
            <button class="btn btn-outline-danger" @click="remove(poke.id)">Eliminar</button>
        </div>
        </li>
    </ul>
    </div>
</template>