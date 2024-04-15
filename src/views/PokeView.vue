<script setup>
    import axios from 'axios';
import { ref } from 'vue';
    import {useRoute, useRouter} from 'vue-router'

    const route = useRoute()
    const router = useRouter()

    const poke = ref ({})

    const back = () => {
        router.push('/pokemons')
    }

    const getData = async () => {
        try {
            const {data} = await axios.get(`https://pokeapi.co/api/v2/pokemon/${route.params.name}`)
            console.log(data);
            poke.value = data;
        } catch (error) {
            console.log(error);
        }
    }

getData()
</script>
<template>

<div class="container">
  <div class="row">
    <div class="col-6 col-sm-4">
        <h3>Poke name: {{ $route.params.name }}</h3>
    </div>
    <div class="col-6 col-sm-3">
        <h3>Datos:</h3>
    </div>

    <!-- Force next columns to break to new line -->
    <div class="w-100"></div>

    <div class="col-6 col-sm-3">
        <img :src="poke.sprites?.front_default" alt="">
    </div>
    <div class="col-6 col-sm-8">
        <h6>{{ poke.abilities}}</h6>
    </div>
    <button @click="back" class="btn btn-primary">POKEAPI</button>
  </div>
</div>
</template>