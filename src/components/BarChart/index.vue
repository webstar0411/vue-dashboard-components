<template>
  <div class="bar-chart-wrapper">
    <h5 class="title">Comprobante</h5>
    <Bar
      :chartData="chartData"
      :chartOptions="chartOptions"
      :width="600"
      class="bar-chart"
    />
    <select class="select">
      <option>Year</option>
      <option>Month</option>
      <option>Day</option>
    </select>
  </div>
</template>

<script setup>
import { defineComponent } from "vue";
import { Bar } from "vue-chartjs";
import { Chart, registerables } from "chart.js";
import "./style.scss";

Chart.register(...registerables);

const { data } = defineProps(["data"]);

const chartData = {
  labels: data.map((item) => item.type),
  datasets: [
    {
      label: "Comprobante",
      data: data.map((item) => item.amount),
      backgroundColor: ["#77CEFF", "#0079AF", "#123E6B", "#97B0C4", "#A5C8ED"],
    },
  ],
};

const chartOptions = {
  responsive: true,
  maintainAspectRatio: false,
  plugins: {
    legend: { display: false },
  },
};
</script>