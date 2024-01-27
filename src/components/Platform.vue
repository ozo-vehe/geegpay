<script setup>
import { ref } from 'vue';

const scroll = ref(false);
const data = [
  {
    name: "book bazaar",
    value: 2500000,
    percentage: 15,
    color: '#6160DC'
  },
  {
    name: "artisan aisle",
    value: 1800000,
    percentage: 10,
    color: '#54C5EB'
  },
  {
    name: "toy troop",
    value: 1200000,
    percentage: 8,
    color: '#FFB74A'
  },
  {
    name: "xstore",
    value: 600000,
    percentage: 5,
    color: '#FF4A55'
  }
]

const formatAmount = (amount) => {
  const add_comma = amount.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ",");
  return add_comma;
}

</script>

<template>
  <section
    class="platform relative w-[600px] h-[440px] py-4 px-6 bg-inherit rounded-[14px] overflow-hidden border bg-white">
    <h3 class="capitalize w-full font-[600] flex items-center mb-5 justify-between text-[18px]">
      <span>platform</span>
      <span class="text-[#34caa5] cursor-pointer" @click="scroll = !scroll">{{ scroll ? 'show less' : 'see all' }}</span>
    </h3>

    <div class="plaform_details_container flex flex-col pr-4 pb-4 gap-6 h-[370px] overflow-y-hidden" :class="{'overflow-y-scroll': scroll}">
      <div class="platform_details flex flex-col gap-4" v-for="(d, index) in data" :key="index">
        <h3 class="capitalize text-[18px] font-[600]">{{ d.name }}</h3>
        <div class="progress_bar bg-gray-100 flex items-center w-full h-3 rounded-[500px] overflow-hidden">
          <span
            :class="{'bg-[#6160DC] w-[60%] rounded-[500px]': d.name.includes('book'), 'bg-[#54C5EB] w-[45%] rounded-[500px]': d.name.includes('artisan'), 'bg-[#FFB74A] w-[35%] rounded-[500px]': d.name.includes('toy'), 'bg-[#FF4A55] w-[25%] rounded-[500px]': d.name.includes('xstore')}"
            class="w-[50px] h-3 block"
          ></span>
        </div>

        <div class="price_percentage flex items-center justify-between">
          <p class="text-[18px] text-[#525252]">${{ formatAmount(d.value) }}</p>
          <p class="text-[18px] text-[#525252]">+{{ d.percentage }}%</p>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.plaform_details_container::-webkit-scrollbar {
  width: 7px;
  /* padding: 5px */
}
/* Track */
.plaform_details_container::-webkit-scrollbar-track {
  box-shadow: inset 0 0 5px rgb(190, 190, 190);
  border-radius: 30px;
}

/* Handle */
.plaform_details_container::-webkit-scrollbar-thumb {
  background: #7e7e7e;
  border-radius: 10px;
}

@media screen and (max-width: 1600px) {
  .platform {
    width: 720px;
    height: 420px;
  }
}

@media screen and (max-width: 1550px) {
  .platform {
    margin-left: 80px;
  }
}

@media screen and (max-width: 1300px) {
  .platform {
    margin-left: 0px;
    width: 720px;
  }
}
@media screen and (max-width: 800px) {
  .platform {
    height: 380px;
    margin: 10px;
    padding-bottom: 40px;
  }
  .platform h3,
  .plaform_details_container h3 {
    font-size: 16px;
  }
  .plaform_details_container p {
    font-size: 14px;
  }
  .platform_details {
    gap: 10px;
  }
}
</style>
