<template>
  <h1>Ma todo-list :</h1>
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
  </div>
</template>

<script setup>
import {ref} from "vue";

const newTodo = ref('')
const todos = ref([])
const addTodo = () => {
  todos.value.push({
    title: newTodo.value,
    completed: false,
    date: Date.now()
  })
  newTodo.value = ''
}
const sortedTodos = computed(() => {
  return todos.value.toSorted((a, b) => a.completed > b.completed ? 1 : -1)

})

</script>

<style>
.completed {
  opacity: .5;
  text-decoration: line-through;
}
</style>