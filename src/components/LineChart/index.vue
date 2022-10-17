/**
 *  CREATED BY webstar0411@gmail.com
 *  CREATED AT 2022.10.14
 *  DESCRIPTION: This component is a line chart and a date picker. Please confirm that you have already installed vue-ctk-date-time-picker and vue-chartjs, chart.js
 *  npm install -S vue-chartjs chart.js vue-ctk-date-time-picker
 *  PROPS: data, 
 */

<template>
  <div class="line-chart-wrapper">
    <div class="line-chart-header">
      <DatePicker
        :range="true"
        :no-button="true"
        v-model="date"
        format="YYYY-MM-DD"
        formatted="YYYY / MM / DD"
        color="purple"
      ></DatePicker>
      <select
        class="select"
        @change="(e) => $emit('onChangeType', e.target.value)"
      >
        <option v-for="(option, name) in options" :value="name" :key="name">
          {{ option }}
        </option>
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
import { ref, reactive, watch, defineEmits } from "vue";
import { Line } from "vue-chartjs";
import { Chart, registerables } from "chart.js";
import DatePicker from "vue-ctk-date-time-picker";
import "vue-ctk-date-time-picker/dist/vue-ctk-date-time-picker.css";
import "./style.scss";

Chart.register(...registerables);

const { data, options } = defineProps(["data", "options"]);
const date = ref({ start: null, end: null });
const emit = defineEmits(["onChangeDate", "onChangeType"]);

watch(date, (newDate, oldDate) => {
  if (newDate.start === null || newDate.end === null) return;
  emit("onChangeDate", newDate);
});

// chart configs
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