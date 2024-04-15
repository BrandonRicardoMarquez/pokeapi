<!-- <template>
    <h1>Poke name {{ $route.params.name }}</h1>
    <h2>poke url {{ pokemon.value }}</h2>
    <ul>
        <li v-for="(poke,index) in pokemon" :key="index">
            <h1>Poke name {{ $route.params.name }}</h1>
            <router-link :to="`/pokemons/${poke.url}`">
                <h2>poke url {{ pokemon.value. poke.url }}</h2>
            </router-link>
        </li>
    </ul>
</template>

<script setup>
import axios from 'axios';
import { ref } from 'vue';
import {RouterLink} from 'vue-router'

    const pokemon = ref([])

    const getData = async () => {
        try{
           const {data} = await axios.get("https://pokeapi.co/api/v2/pokemon/$route.params.name")
           pokemon.value = data.results
        } catch (error) {
            console.log(error)
        }
    }

    getData();
</script> -->