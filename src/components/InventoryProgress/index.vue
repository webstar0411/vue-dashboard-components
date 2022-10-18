<template>
  <div class="inventory-progress">
    <p class="inventory-header">
      <span class="title">Inventario Hidrocaburos</span>
      <select
        class="company"
        @change="(e) => $emit('onChange', e.target.value)"
      >
        <option v-for="(option, name) in company" :value="name" :key="name">
          {{ option }}
        </option>
      </select>
    </p>
    <InventoryItem
      v-for="item in data"
      :key="item.type"
      :data="item"
    ></InventoryItem>
  </div>
</template>

<script setup>
import InventoryItem from "./item.vue";
import "./style.scss";

const { data, company } = defineProps(["data", "company"]);
</script>