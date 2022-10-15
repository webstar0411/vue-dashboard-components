<template>
  <div class="line-chart-wrapper">
    <div class="line-chart-header">
      <DatePicker
        :range="true"
        v-model="date"
        format="YYYY-MM-DD"
        formatted="YYYY / MM / DD"
        color="purple"
      ></DatePicker>
      <select class="select">
        <option>All</option>
        <option>Business1</option>
        <option>Business2</option>
      </select>
    </div>
    <Line
      :chartData="chartData"
      :chartOptions="chartOptions"
      :plugins="plugin"
      :width="600"
      class="line-chart"
    />
  </div>
</template>

<script setup>
import { ref } from "vue";
import { Line } from "vue-chartjs";
import { Chart, registerables } from "chart.js";
import DatePicker from "vue-ctk-date-time-picker";
import "vue-ctk-date-time-picker/dist/vue-ctk-date-time-picker.css";
import "./style.scss";

Chart.register(...registerables);

const { data } = defineProps(["data"]);
const date = ref(null);

const chartData = {
  labels: data.map((item) => item.date),
  datasets: [
    {
      label: "Sales",
      data: data.map((item) => item.sale),
      backgroundColor: "#f87979",
    },
    {
      label: "Purchase",
      data: data.map((item) => item.purchase),
      backgroundColor: "#981235",
    },
  ],
};

const chartOptions = {
  responsive: true,
  maintainAspectRatio: false,
  plugins: {
    paddingBelowLegends: false,
    legend: {
      align: "end",
      labels: {
        font: { size: 14 },
      },
    },
  },
};
const plugin = [
  {
    id: "increase-legend-spacing",
    beforeInit(chart) {
      const originalFit = chart.legend.fit;
      chart.legend.fit = function fit() {
        originalFit.bind(chart.legend)();
        this.height += 50;
      };
    },
  },
];
</script>