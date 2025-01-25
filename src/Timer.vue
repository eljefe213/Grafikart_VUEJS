<template>
  <div>
    Temps : {{ time }}
  </div>
</template>
<script setup>
import {onMounted, onUnmounted, ref} from "vue";

const time = ref(0)
let timer

onMounted(() => {
  timer =   setInterval(() => {
    time.value++
  }, 1_000)
})

onUnmounted(() => {
  clearInterval(timer)
})
</script>