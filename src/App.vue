<template>
  <p>Compteur : {{ count }}</p>
  <button @click="increment" >Incrémenter</button>
  <button @click="decrement" >Decrémenter</button>
  <button @click="sortMovie">Réorganiser</button>
  <ul>
    <li v-for="movie in movies"
    :key="movie"> {{ movie }}
      <button @click="deleteMovie(movie)">Supprimer</button>
    </li>
  </ul>
</template>

<script setup>
import {ref} from "vue";

const count = ref(0)
const movies = ref([
    'Matrix',
    'Lilo & Stitch',
    'Titanic'
])
const increment = (event) => {
  count.value++
}
const decrement = (event) => {
  count.value--
}
const deleteMovie = (movie) => {
  movies.value = movies.value.filter(m => m !== movie)
}
const sortMovie = () => {
  movies.value.sort((a,b) => a > b ? 1 : -1)
}
</script>

<style>
.active {
  color: red;
}
</style>