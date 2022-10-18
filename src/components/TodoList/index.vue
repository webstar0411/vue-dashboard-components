<template>
  <div class="todo-list">
    <div class="todo-header">
      <span class="title">Incidencias</span>
      <span class="svg-button">
        <div class="todo-tooltip">
          <img
            :src="FileSVG"
            @click="() => $emit('onChange', 'tasks', 'tasks')"
          />
          <span class="tooltiptext">Task</span>
        </div>
        <div class="todo-tooltip">
          <img
            :src="FileOutlineSVG"
            @click="() => $emit('onChange', 'tasks', 'recommandation')"
          />
          <span class="tooltiptext">Recommendation</span>
        </div>
        <div class="todo-tooltip">
          <img
            :src="BagSVG"
            @click="() => $emit('onChange', 'tasks', 'issue')"
          />
          <span class="tooltiptext">Issue</span>
        </div>
      </span>
      <select @change="(e) => $emit('onChange', 'company', e.target.value)">
        <option v-for="(option, name) in company" :value="name" :key="name">
          {{ option }}
        </option>
      </select>
    </div>
    <div class="todo-wrapper">
      <TodoItem v-for="(item, key) in data" :data="item" :key="key"></TodoItem>
    </div>
  </div>
</template>

<script setup>
import TodoItem from "./TodoItem.vue";
import FileSVG from "./svg/file.svg";
import FileOutlineSVG from "./svg/fileOutline.svg";
import BagSVG from "./svg/bag.svg";
import "./style.scss";

const { data, company } = defineProps(["data", "company"]);
</script>