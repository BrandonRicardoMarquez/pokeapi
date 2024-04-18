<script setup>
import {useFavoritosStore} from '@/store/favoritos'
import { storeToRefs } from 'pinia';

const useFavoritos = useFavoritosStore()

const {favoritos} = storeToRefs(useFavoritos)
</script>

<template>
    <div class="container bg-white">
    <h1 >Favoritos</h1>
    <h2 v-if="favoritos.length === 0" > Sin favoritos</h2>
    <ul class="list-group text-center" v-else>
        <li class="list-group-item" v-for="poke 
        in favoritos" 
        :key="poke.id">
        {{ poke.name }}
        </li>
    </ul>
    </div>
</template>