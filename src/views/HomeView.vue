<script setup>
import { ref } from 'vue'

function generateData(count, yrange) {
  var i = 0;
  var series = [];
  while (i < count) {
    var x = (i + 1).toString();
    var y =
      Math.floor(Math.random() * (yrange.max - yrange.min + 1)) + yrange.min;

    series.push({
      x: x,
      y: y
    });
    i++;
  }
  return series;
}

const series = [{
  name: 'Sun',
  data: generateData(9, {
    min: -30,
    max: 55
  })
},
{
  name: 'Satur',
  data: generateData(9, {
    min: -30,
    max: 55
  })
},
{
  name: 'Frid',
  data: generateData(9, {
    min: -30,
    max: 55
  })
},
{
  name: 'Thurs',
  data: generateData(9, {
    min: -30,
    max: 55
  })
},
{
  name: 'Wed',
  data: generateData(9, {
    min: -30,
    max: 55
  })
},
{
  name: 'Tues',
  data: generateData(9, {
    min: -30,
    max: 55
  })
},
{
  name: 'Mon',
  data: generateData(9, {
    min: -30,
    max: 55
  })
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
  },
  chart: {
    height: 350,
    type: 'heatmap',
  },
  plotOptions: {
    heatmap: {
      shadeIntensity: 0.5,
      radius: 0,
      useFillColorAsStroke: false,
      colorScale: {
        ranges: [{
          from: -30,
          to: 5,
          name: 'done',
          color: '#00A100'
        },
        {
          from: 6,
          to: 20,
          name: 'last',
          color: '#CBD5E1'
        },
        {
          from: 21,
          to: 45,
          name: 'sent',
          color: '#FFB200'
        },
        {
          from: 46,
          to: 55,
          name: 'fail',
          color: '#FF0000'
        }
        ]
      }
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
    text: 'HeatMap Chart with Color Range'
  },
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