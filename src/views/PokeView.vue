<script setup>
    // import axios from 'axios';
    //  import { ref,watch } from 'vue';
    import {useRoute, useRouter} from "vue-router"
    import { useGetData} from '@/composables/getData'
    import {useFavoritosStore} from '@/store/favoritos'
    import { watch } from 'vue' // Importa watch de 'vue'
    

    const route = useRoute()
    const router = useRouter()
    const useFavoritos = useFavoritosStore()

    const {add, findPoke} = useFavoritos

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


    watch(route, (ewX) => {
        getData(`https://pokeapi.co/api/v2/pokemon/${route.params.name}`)
    })
    getData(`https://pokeapi.co/api/v2/pokemon/${route.params.name}`)
  // Observa cambios en la ruta y llama a la función watchRouteChanges
 
</script>
<template>
<p v-if="loading">Estoy cargando hehehe </p>
<div class="alert alert-danger mt-3" v-if="error"> {{ error }} </div>
<div class="container bg-white " v-if=data>
  <div class="row">
    <div class="col-6 col-sm-4 ">
        <h3>Poke name: <br/> 
            <!-- {{ $route.params.name }}  -->
            {{ data.name }}</h3>
        
    </div>
    <div class="col-6 col-sm-3">
        <h3>Datos: </h3> 
    </div>

    <!-- Force next columns to break to new line -->
    <div class="w-100"></div>

    <div class="col-6 col-sm-3">
        <img :src="data.sprites?.front_default" alt="">
    </div>
    <div class="col-6 col-sm-8" >
        <ul class="list-group">
            <h2>Type:</h2>
            <li class="list-group-item" v-for="(type,index) in data.types" :key="index" :class="type.type.name ">
                <span>{{ type.type.name}} </span>
            </li>
        </ul>
        <ul class="list-group">
            <h2>Stats:</h2>
                <li class="list-group-item"
                v-for="(stat, key) in data.stats"
                :key="key"
                >
                <span>{{ stat.stat.name}} -> {{stat.base_stat }}</span>
                
                </li>
                <button :disabled="findPoke(data.name)" class="btn btn-primary btn-block mt-3" @click="add(data)">Agregar Favoritos</button> <br>
        </ul>
        <!-- <span>{{ type.type.name}} </span> -->
    </div>
  </div>
</div>
<div class="container">
    <div class="text-center">
        <button @click="back" class="btn btn-primary btn-block me-2">POKEAPI</button>
    </div>
</div>
</template>