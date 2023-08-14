<script setup>
import { ref, onMounted, onBeforeUnmount } from 'vue';

let chart = null

const dataset = [
  300, 50, 100
]

const data = {
  labels: [
    'Magenta',
    'Lime',
    'Yellow'
  ],
  datasets: [{
    label: 'My First Dataset',
    data: dataset,
    backgroundColor: [
      'rgb(255,0,255)',
      'rgb(0, 255, 0)',
      'rgb(255, 205, 86)',
    ],
    hoverOffset: 4
  }]
};

const config = {
  type: 'pie',
  data: data,
};

onMounted(() => {
  const ctx = document.getElementById('chart')
  chart = new Chart(ctx, config)
})


onBeforeUnmount(() => {
  if (chart) {
    chart.destroy();
    chart = null;
  }
});

</script>

<template>
  <h1 class="text-4xl">Pie Chart</h1>
  <div class=" mx-auto w-[400px] h-[400px] bg-gray-400">
    <canvas id="chart">
    </canvas>
  </div>
</template>

<style scoped></style>
