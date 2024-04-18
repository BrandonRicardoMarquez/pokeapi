<script setup>
    // import axios from 'axios';
    // import { ref } from 'vue';
    import {useRoute, useRouter} from "vue-router"
    import { useGetData} from '@/composables/getData'
    import {useFavoritosStore} from '@/store/favoritos'
    

    const route = useRoute()
    const router = useRouter()
    const useFavoritos = useFavoritosStore()
    

    const {add} = useFavoritos

    const {getData, data, loading, error } = useGetData();

    // const poke = ref ({})

    const back = () => {
        router.push('/pokemons')
    }

    // const getData = async () => {
    //     try {
    //         const {data} = await axios.get(`https://pokeapi.co/api/v2/pokemon/${route.params.name}`)
    //         console.log(data);
    //         poke.value = data;
    //     } catch (error) {
    //         console.log(error);
    //         poke.value = null;
    //     }
    // }

getData(`https://pokeapi.co/api/v2/pokemon/${route.params.name}`)
</script>
<template>
<p v-if="loading">Estoy cargando hehehe </p>
<div class="alert alert-danger mt-3" v-if="error"> {{ error }} </div>
<div class="container bg-white " v-if=data>
  <div class="row">
    <div class="col-6 col-sm-4 ">
        <h3>Poke name: <br/> {{ $route.params.name }}</h3>
        <button class="btn btn-primary btn-block mt-3" @click="add(data)">Agregar Favoritos</button>
    </div>
    <div class="col-6 col-sm-3">
        <h3>Datos:</h3>
    </div>

    <!-- Force next columns to break to new line -->
    <div class="w-100"></div>

    <div class="col-6 col-sm-3">
        <img :src="data.sprites?.front_default" alt="">
    </div>
    <div class="col-6 col-sm-8">
        <h6>{{ data.abilities}}</h6>
    </div>
  </div>
</div>
<div class="container">
    <div class="text-center">
        <button @click="back" class="btn btn-primary btn-block">POKEAPI</button>
    </div>
</div>
</template>