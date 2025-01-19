<template>
  <p>Compteur : {{ count }}<div v-html="firstName"></div> </p>
  <button @click="increment" >Incrémenter</button>
  <button @click="decrement" >Decrémenter</button>
</template>

<script setup>
import {ref} from "vue";

const count = ref(0)
const firstName = '<span>Demo</span>'
const increment = (event) => {
  count.value++
}
const decrement = (event) => {
  count.value--
}
</script>

<style>
.active {
  color: red;
}
</style>