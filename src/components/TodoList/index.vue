<template>
  <div class="todo-list">
    <div class="todo-header">
      <span class="title">Incidencias</span>
      <span class="svg-button">
        <div class="todo-tooltip">
          <img v-if="taskIdx === 0" :src="SuccessSVG" class="success" />
          <img
            :src="FileSVG"
            @click="() => ($emit('onChange', 'tasks', 'tasks'), (taskIdx = 0))"
          />
          <span class="tooltiptext">Task</span>
        </div>
        <div class="todo-tooltip">
          <img v-if="taskIdx === 1" :src="SuccessSVG" class="success" />
          <img
            :src="FileOutlineSVG"
            @click="
              () => (
                $emit('onChange', 'tasks', 'recommandation'), (taskIdx = 1)
              )
            "
          />
          <span class="tooltiptext">Recommendation</span>
        </div>
        <div class="todo-tooltip">
          <img v-if="taskIdx === 2" :src="SuccessSVG" class="success" />
          <img
            :src="BagSVG"
            @click="() => ($emit('onChange', 'tasks', 'issue'), (taskIdx = 2))"
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
import { ref } from "vue";
import TodoItem from "./TodoItem.vue";
import FileSVG from "./svg/file.svg";
import FileOutlineSVG from "./svg/fileOutline.svg";
import BagSVG from "./svg/bag.svg";
import SuccessSVG from "./svg/success.svg";

import "./style.scss";

const taskIdx = ref(0);

const { data, company } = defineProps(["data", "company"]);
</script>