<script setup>
import {useCounterStore} from "@/store/counter.js"
const useCounter = useCounterStore ()
</script>

<template>
    <h1>🍔 HOME 🍔 <br> counter: {{ useCounter.count }}</h1> 
    <button @click="useCounter.increment" class="btn btn-success">Incrementar</button>
</template>
