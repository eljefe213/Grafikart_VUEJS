<template>
  <p>Compteur : {{ count }}</p>
  <button @click="increment" >Incrémenter</button>
  <button @click="decrement" >Decrémenter</button>
  <hr>
  <button @click="sortMovie">Réorganiser</button>
  <form action="" @submit.prevent="addMovie">
    <input type="text" placeholder="Nouveau film" v-model="movieName">
    <button>Ajouter</button>
  </form>
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
const movieName = ref('')
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
const addMovie = () => {
  movies.value.push(movieName.value)
  movieName.value = ''
}
</script>

<style>
.active {
  color: red;
}
</style>