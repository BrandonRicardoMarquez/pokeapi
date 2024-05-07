<script setup>
// import axios from 'axios';
// import { ref } from 'vue';
import {RouterLink} from 'vue-router'
import {useGetData} from '@/composables/getData'


    // const pokemons = ref([])

    const { data, getData, loading, error } = useGetData()

    // const getData = async () => {
    //     try{
    //        const {data} = await axios.get("https://pokeapi.co/api/v2/pokemon")
    //        pokemons.value = data.results
    //     } catch (error) {
    //         console.log(error)
    //     }
    // }

    getData("https://pokeapi.co/api/v2/pokemon");
</script>

<template>
    <h1 class="text-warning">Pokemons</h1>
    <br>
    <p v-if="loading">Estoy cargando hehehe </p>
    <div class="alert alert-danger mt-3" v-if="error"> {{ error }} </div>
    <div v-if="data">
        <ul class="list-group text-center">
            <li v-for="(poke,index) in data.results" :key="index" class="list-group-item">
                <button class="btn btn-outline-dark btn-lg  no-underline btn-symmetrical" >
                <router-link :to="`/pokemons/${poke.name}`" class="text-warning">
                    {{ poke.name }}
                </router-link>
                </button>
                <!-- <router-link :to="`/pokemons/${poke.url}`">
                    {{ poke.url }}
                </router-link> -->
            </li>
        </ul>
        <button :disabled="!data.previous"
                class="btn btn-warning me-2" 
                @click="getData(data.previous)">Previous</button>
        <button 
                :disabled="!data.next"
                class="btn btn-primary" 
                @click="getData(data.next)">Next</button>
    </div>
</template>

<style>
/* Estilo personalizado para quitar el subrayado y poner en negrita dentro de un botón */
    .no-underline {
      text-decoration: none;
      font-weight: bold;
    }
    /* Estilo personalizado para botón con tamaño simétrico */
    .btn-symmetrical {
      width: 150px; /* Ancho deseado */
      height: 50px; /* Alto deseado */
      /* Puedes ajustar el tamaño según tus necesidades */
    }
    body {
    background-image: url('https://cdn.hobbyconsolas.com/sites/navi.axelspringer.es/public/media/image/2019/08/pokemon_10.jpg?tf=3840x');
    background-size: cover;
    background-repeat: no-repeat;
    }
    
</style>