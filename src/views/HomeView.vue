<script setup>
import { ref } from 'vue'



const series = [{
  name: 'Sun',
  data: [{ x: 1, y: 2 }, { x: 1, y: 2 }, { x: 2, y: 4 }]
},
{
  name: 'Sat',
  data: [{ x: 1, y: 1 }]
},
{
  name: 'Fri',
  data: [{ x: 1, y: 1 }]

},
{
  name: 'Thu',
  data: [{ x: 1, y: 1 }]
},
{
  name: 'Wed',
  data: [{ x: 1, y: 1 }]
},
{
  name: 'Tue',
  data: [{ x: 1, y: 1 }]
},
{
  name: 'Mon',
  data: [{ x: 1, y: 1 }]
},
];
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
          name: 'unfinished',
          color: '#CBD5E1'
        },
        ]
      }
    }
  },
  tooltip: {
    custom: function ({ series, seriesIndex, dataPointIndex, w }) {
      return '<div class="p-1 text-xs tracking-tight">Monday, October 12, 2023</div>'
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
// TODO: зробити як на github. Додати hover action для кожного квадрату з інформацією про дату.


// const data = ref("null")
// const error = ref(null)

// fetch(`${import.meta.env.VITE_API_PATH}/acceptances`)
//   .then((res) => {
//     if (res.status === 401) {
//       throw new Error(res.statusText)
//     }
//   })
//   .catch((err) => {
//     error.value = err
//   })
</script>

<template>
  <main class="max-w-[380px] mx-auto">
    <div id="chart">
      <apexchart type="heatmap" height="350" :options="chartOptions" :series="series"></apexchart>
    </div>

  </main>
</template>