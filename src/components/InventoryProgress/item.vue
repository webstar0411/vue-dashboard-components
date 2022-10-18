<template>
  <div class="inventory-item">
    <div class="inventory-name" :style="{ background: data.color }">
      {{ data.type }}
    </div>
    <span class="inventory-percent">{{ data.percent }}%</span>
    <div class="animated-progress" :style="{ background: data.bg }">
      <div class="wrapper">
        <span
          class="rate"
          :style="{ width: data.percent + '%', background: data.light }"
        >
        </span>
      </div>
      <p class="progress-label">
        <label>{{ data.gls }} Gls</label>
        <label>{{ 100 - data.percent }}%</label>
      </p>
    </div>
  </div>
</template>

<script setup>
const { data } = defineProps(["data"]);
</script>