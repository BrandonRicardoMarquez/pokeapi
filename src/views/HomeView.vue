<script setup>
import {useCounterStore} from "@/store/counter.js"
const useCounter = useCounterStore ()
</script>

<template>
  <div class="container bg-white text-center">
    <h1>🍔 HOME 🍔 <br> Counter: {{ useCounter.count }}</h1>
    <h2>Double: {{ useCounter.double }}</h2> 
    <button @click="useCounter.increment" class="btn btn-success">Incrementar</button>
  </div>
</template>
