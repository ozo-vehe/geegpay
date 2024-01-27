<script setup>
import red_graph from '../assets/icons/red-graph.png';
import green_graph from '../assets/icons/green-graph.png';
import tick_icon from '../assets/icons/box-tick.png';
import refund_icon from '../assets/icons/3d-rotate.png';
import cart_icon from '../assets/icons/shopping-cart.png';
import coin_icon from '../assets/icons/coin.png';
const data = [
  {
    title: "Total Order",
    value: 350,
    icon: tick_icon,
    percentage: 23.5,
    graph: green_graph
  },
  {
    title: "Total Refund",
    value: 350,
    icon: refund_icon,
    percentage: 23.5,
    graph: red_graph
  },
  {
    title: "Average Sales",
    value: 1567,
    icon: cart_icon,
    percentage: 23.5,
    graph: red_graph
  },
  {
    title: "Total Income",
    value: 350,
    icon: coin_icon,
    percentage: 23.5,
    graph: green_graph
  }
]
</script>

<template>
  <section
    class="relative w-[600px] h-[500px] mt-5 flex gap-5 flex-wrap items-center market bg-inherit rounded-[14px] overflow-hidden">
    <div class="dashboard_card w-[48.3%] h-[48%] p-4 rounded-[14px] border border-[#edf2f7] bg-white" v-for="(d, index) in data"
      :key="index">
      <div class="images flex justify-between items-start mb-4">
        <img class="border rounded-full w-10 p-2" :src="d.icon" alt="Tick icon">
        <img class="h-full" :src="d.graph" alt="Green graph">
      </div>

      <div class="card_details mb-[26px]">
        <h3 class="text-[18px] text-[#898989]">{{ d.title }}</h3>
        <p class="text-[24px] text-[#3a3f51] font-[600]">{{ d.title.includes("Income") ? `$${d.value}.00` : d.value }}</p>
      </div>

      <div class="card_status">
        <p class="flex gap-3 text-[14px] inter">
          <span class="rounded-[100px] py-1 px-2 flex items-center gap-1 text-[12px]"
            :class="{ 'bg-[#ed544e1f] text-red-500': d.graph.includes('red'), 'bg-[#34caa51f] text-green-500': d.graph.includes('green') }">
            <svg v-if="d.graph.includes('green')" xmlns="http://www.w3.org/2000/svg" width="10" height="6"
              viewBox="0 0 10 6" fill="none">
              <path d="M0.5 5.5L3.5 2.5L5.5 4.5L9.5 0.5" stroke="#34CAA5" stroke-linecap="round"
                stroke-linejoin="round" />
              <path d="M6 0.5H9.5V4" stroke="#34CAA5" stroke-linecap="round" stroke-linejoin="round" />
            </svg>

            <svg v-else xmlns="http://www.w3.org/2000/svg" width="10" height="6" viewBox="0 0 10 6" fill="none">
              <path d="M0.5 0.5L3.5 3.5L5.5 1.5L9.5 5.5" stroke="#ED544E" stroke-linecap="round"
                stroke-linejoin="round" />
              <path d="M6 5.5H9.5V2" stroke="#ED544E" stroke-linecap="round" stroke-linejoin="round" />
            </svg>
            {{ d.percentage }}%
          </span>
          vs. previous month
        </p>
      </div>
    </div>
  </section>
</template>

<style scoped>
/* body {
  text: #34caa51f;
} */
@media screen and (max-width: 1600px) {
  .market {
    width: 720px;
    height: 420px;
  }
}

@media screen and (max-width: 1550px) {
  .market {
    margin-left: 80px;
  }
}

@media screen and (max-width: 1300px) {
  .market {
    margin-left: 0px;
    width: 720px;
  }
}

@media screen and (max-width: 800px) {
  .market {
    /* height: 320px; */
    margin: 10px;
  }
  .dashboard_card {
    width: 48%;
  }
}
</style>
