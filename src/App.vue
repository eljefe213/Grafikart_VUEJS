<template>
  <h1>Ma todolist :</h1>
  <Layout>
    <template #header>En tête</template>
    <template #aside>Sidebar</template>
    <template #main>Main</template>
    <template #footer>Footer</template>
  </Layout>
  <form @submit.prevent="addTodo">
    <fieldset role="group">
      <input type="text" placeholder="Tâche à effectuer" v-model="newTodo">
      <button :disabled="newTodo.length === 0">Ajouter</button>
    </fieldset>
  </form>
  <div v-if="todos.length === 0">Vous n'avez pas de tâches à faire</div>
  <div v-else>
    <ul>
      <li v-for="todo in sortedTodos" :key="todo.date" :class="{completed: todo.completed}">
        <checkbox :label="todo.title" v-model="todo.completed "/>
      </li>
    </ul>
    <label>
      <input type="checkbox" v-model="hideCompleted">
      Masquer les tâches complétées
    </label>
    <p v-if="remainingTodos > 0">
      {{ remainingTodos}} tâche{{ remainingTodos > 1 ? 's' : ''}} à faire
    </p>
    <checkbox label="Bonjour"/>
  </div>
</template>

<script setup>
import {computed, ref} from "vue";
import Checkbox from './Checkbox.vue';
import Button from './Button.vue';
import Layout from "@/Layout.vue";

const newTodo = ref('')
const hideCompleted = ref(false)
const todos = ref([{
  title: 'Tâche de test',
  completed: true,
  date: 1,
},{
  title: 'Tâche à faire',
  completed: false,
  date: 2,
}])
const addTodo = () => {
  todos.value.push({
    title: newTodo.value,
    completed: false,
    date: Date.now()
  })
  newTodo.value = ''
}
const sortedTodos = computed(() => {
   const sortedTodos = todos.value.toSorted((a, b) => a.completed > b.completed ? 1 : -1)
  if ( hideCompleted.value === true) {
    return sortedTodos.filter(t => t.completed === false)
  }
  return sortedTodos
})
const remainingTodos = computed(() => {
  return todos.value.filter(t => t.completed === false).length
})
</script>

<style>
.completed {
  opacity: .5;
  text-decoration: line-through;
}
</style>