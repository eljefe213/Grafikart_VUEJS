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
 const emits = defineEmits(['check', 'uncheck'])
</script>