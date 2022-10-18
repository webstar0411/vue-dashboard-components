<template>
  <div :class="['todo-item', data.type === 0 ? 'checked' : 'admin']">
    <p class="todo-title">
      <span>{{ data.date }}</span>
      <span>|</span>
      <span>{{ data.hour }}</span>
      <span>|</span>
      <span>{{ data.company }}</span>
      <span>|</span>
      <span>{{ data.worker }}</span>
    </p>
    <p class="todo-content">LLega Tarde al Trabajo</p>
  </div>
</template>

<script setup>
const { data } = defineProps(["data"]);
</script>