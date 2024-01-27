<script setup>
import Chart from 'chart.js/auto';
import { onMounted, ref } from 'vue';

const data = [
  { month: "Jan", amount: 8000 },
  { month: "Feb", amount: 21000 },
  { month: "Mar", amount: 6000 },
  { month: "Apr", amount: 30000 },
  { month: "May", amount: 9000 },
  { month: "Jun", amount: 45000 },
  { month: "Jul", amount: 9000 },
  { month: "Aug", amount: 22000 },
  { month: "Sep", amount: 32000 },
  { month: "Oct", amount: 7000 },
  { month: "Nov", amount: 30000 },
  { month: "Dec", amount: 26000 }
];

const chart = ref(null);
const barchart = ref(null)
onMounted(() => {
  createChart();
});

const screen_width = ref(0);
window.addEventListener('resize', function() {
  screen_width.value = window.innerWidth;
})

onMounted(() => {
  screen_width.value = window.innerWidth
})



const createChart = () => {
  const ctx = barchart.value.getContext('2d');
  const gradient = ctx.createLinearGradient(0, 0, 0, 400);
  gradient.addColorStop(0, '#34CAA5');
  gradient.addColorStop(1, '#34caa51a');

  chart.value = new Chart(barchart.value.getContext('2d'), {
    type: 'bar',
    data: {
      labels: data.map(row => row.month),
      datasets: [
        {
          data: data.map(row => row.amount),
          borderRadius: 50,
          backgroundColor: 'rgba(52, 202, 165, 0.10)',
          hoverBackgroundColor: gradient,
          barThickness: 40,
        }
      ]
    },
    options: {
      scales: {
        y: {
          beginAtZero: true,
          suggestedMax: 50000,
          border: {
            dash: [2, 4]
          },
        },
        x: {
          grid: {
            display: false,
            drawBorder: false,
          }
        }
      },
      plugins: {
        legend: {
          display: false
        }
      }
    },
  });
}
</script>

<template>
  <section
    class="w-[830px] border relative h-[500px] flex flex-wrap items-center justify-center barchart ml-[90px] my-5 bg-white rounded-[14px] overflow-y-hidden overflow-x-auto px-4 py-5">
    <div class="barchart_header w-full flex items-center justify-between">
      <h3 class="capitalize w-full font-[600] flex items-center justify-between text-[18px]">
        sales trends
      </h3>
      <div class="sorting flex items-center justify-end gap-[10px] w-[300px]">
        <p class="text-[18px]">Sort by:</p>
        <div class="sort_selection pr-2 rounded-[20px] border border-[#e1dfdf] bg-white">
          <select class="capitalize bg-inherit outline-none rounded-[20px] px-3 py-2 w-full h-full" name="sorting" id="sorting">
            <option value="daily">daily</option>
            <option value="weekly">weekly</option>
            <option value="monthly">monthly</option>
            <option value="yearly">yearly</option>
          </select>
        </div>
      </div>
    </div>

    <div class="barchat_container w-full h-[400px]">
      <canvas ref="barchart"></canvas>
    </div>
  </section>
</template>

<style scoped>
body {
  color: #34caa51a;
}

canvas {
  width: 100% !important;
}

@media screen and (max-width: 1600px) {
  .barchart {
    margin-left: 80px;
    width: 720px;
    height: 420px;
  }
}

@media screen and (max-width: 1300px) {
  .table_data {
    margin-left: 0px;
    width: 600px;
  }
  .barchart {
    margin-left: 0px;
  }
}
@media screen and (max-width: 800px) {
  .barchart {
    height: 400px;
    margin: 10px;
  }
  .barchart h3 {
    font-size: 16px;
  }
  .sorting p {
    font-size: 14px;
  }
  .sorting select {
    font-size: 14px;
  }
}

@media screen and (max-width: 700px) {
  .barchart {
    height: 350px;
  }
}
@media screen and (max-width: 650px) {
  .barchart {
    height: 340px;
  }
}
</style>
