<script setup>
import { inject } from "vue";
import json from "../../response.json";

const WebApp = inject("WebApp");

const chartOptions = {
  xaxis: {
    labels: {
      show: false,
    },
    axisTicks: {
      show: false,
    },
    tooltip: {
      enabled: false,
    },
  },
  legend: {
    position: 'bottom',
    horizontalAlign: 'right',
    itemMargin: {
      horizontal: 13,
    },
  },
  chart: {
    height: 350,
    type: 'heatmap',
    toolbar: false
  },
  plotOptions: {
    heatmap: {
      shadeIntensity: 0.5,
      radius: 0,
      useFillColorAsStroke: false,
      colorScale: {
        ranges: [{
          from: 1,
          to: 1,
          name: 'done',
          color: '#00A100'
        },
        {
          from: 2,
          to: 2,
          name: 'fail',
          color: '#FF0000'
        },
        {
          from: 3,
          to: 3,
          name: 'sent',
          color: '#FFB200'
        },
        {
          from: 4,
          to: 4,
          name: 'pending',
          color: '#CBD5E1'
        },
        ]
      }
    }
  },
  tooltip: {
    custom: function ({ seriesIndex, dataPointIndex }) {
      return `<div class="p-1 text-xs tracking-tight">${json.series[seriesIndex].data[dataPointIndex].date}</div> `
    }
  },
  dataLabels: {
    enabled: false
  },
  stroke: {
    width: 1,
  },
  grid: {
    show: false,
  },
  title: {
    text: '12.10.2023 — 20.11.2023',
    align: 'center',
    offsetX: 14,
    offsetY: 14,
  }
};
</script>

<template>
  <main class="max-w-[380px] mx-auto">
    <div id="chart" v-if="WebApp.initData !== ''">
      <apexchart type="heatmap" height="350" :options="chartOptions" :series="json.series"></apexchart>
    </div>
    <div v-else>
      <h1>Hello, User!</h1>
      <p>You need to open Telegram bot</p>
      <a href="https://t.me/batutnik_bot">Batut</a>
    </div>
  </main>
</template>