<template>
<label>
  <input type="checkbox">
  {{ label }}
</label>
</template>
<script setup>
defineProps({
  label: String
})
defineEmits(['check', 'uncheck'])
</script>