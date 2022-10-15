/**
 *  CREATED AT 2022.10.12
 *  CREATED BY webstar0411@gmail.com
 */


<template>
  <section>
    <main class="container container-fluid mt-3">
      <div class="text-center">
        <SummaryCard
          v-for="(item, index) in cardDatas"
          :data="item"
          :key="index"
        ></SummaryCard>
      </div>

      <div class="text-center mt-3">
        <BarChart :data="barChartData"></BarChart>
      </div>

      <div class="text-center mt-3">
        <LineChart :data="lineData"></LineChart>
      </div>
    </main>
  </section>
</template>

<script setup>
import { ref } from "vue";
import SummaryCard from "./components/SummaryCard/index.vue";
import BarChart from "./components/BarChart/index.vue";
import LineChart from "./components/LineChart/index.vue";

import sampleData from "./sampleData.json";

const barChartData = ref(sampleData.barChartData);
const cardDatas = ref(sampleData.cardDatas);
const lineData = ref(sampleData.lineData);
</script>
