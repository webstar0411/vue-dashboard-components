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
        <BarChart
          :data="barChartData"
          :options="dateTypes"
          @onChange="handleBarChart"
        ></BarChart>
      </div>

      <div class="text-center mt-3">
        <LineChart
          :data="lineData"
          @onChangeDate="handleDate"
          @onChangeType="handleLineChartType"
          :options="businessTypes"
        >
        </LineChart>
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

const businessTypes = {
  all: "All",
  business1: "BUSINESS 1",
  business2: "BUSINESS 2",
};

const dateTypes = {
  year: "YEAR",
  month: "MONTH",
  day: "DAY",
};

const handleBarChart = (val) => {
  console.log(val);
};

const handleDate = (date) => {
  console.log(date);
};

const handleLineChartType = (val) => {
  console.log(val);
};
</script>
