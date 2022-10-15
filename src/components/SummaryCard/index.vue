/**
 *  CREATED AT 2022.10.14
 *  CREATED BY webstar0411@gmail.com
 */

<template>
  <div class="summary-card-item">
    <h5 class="card-title">
      {{ data.type }}
    </h5>
    <hr />
    <p class="today">
      {{ data.today }}
    </p>
    <div class="animated-progress progress-blue">
      <div class="wrapper">
        <span class="rate" :style="{ width: data.progress + '%' }"> </span>
      </div>
    </div>
    <p class="yesterday">Ayer: {{ data.yesterday }}</p>
  </div>
</template>

<script setup>
import "./style.scss";

const props = defineProps(["data"]);

const data = props.data;
</script>