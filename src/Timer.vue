<template>
  <div>
    Temps : {{ time }}
  </div>
</template>
<script setup>
import {ref} from "vue";

const time = ref(0)
</script>