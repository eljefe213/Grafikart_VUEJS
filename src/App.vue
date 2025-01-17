<template>
  <p :style="{color: 'red'}">Compteur : {{ count }} </p>
  <button @click="increment" >Incrémenter</button>
  <button @click="decrement" >Decrémenter</button>
</template>

<script setup>
import {ref} from "vue";

const count = ref(0)
const increment = (event) => {
  count.value++
}
const decrement = (event) => {
  count.value--
}
</script>
