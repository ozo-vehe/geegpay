<script setup>
import user_01 from '../assets/icons/user-01.png';
import user_02 from '../assets/icons/user-02.png';
import user_03 from '../assets/icons/user-03.png';
import user_04 from '../assets/icons/user-04.png';
import user_05 from '../assets/icons/user-05.png';
import user_06 from '../assets/icons/user-01.png';
import user_07 from '../assets/icons/user-02.png';
import user_08 from '../assets/icons/user-03.png';
import user_09 from '../assets/icons/user-04.png';
import user_10 from '../assets/icons/user-05.png';
import { ref } from 'vue';

// const orders = data.last_orders;
const scroll = ref(false);

const orders = [
  {
    image: user_01,
    name: "marcus bergson",
    date: "Nov 15, 2023",
    amount: 80000,
    status: "paid",
    invoice: "www.filepath.com"
  },
  {
    image: user_02,
    name: "jaydon vaccaro",
    date: "Nov 15, 2023",
    amount: 150000,
    status: "refund",
    invoice: "www.filepath.com"
  },
  {
    image: user_03,
    name: "corey schleifer",
    date: "Nov 14, 2023",
    amount: 87000,
    status: "paid",
    invoice: "www.filepath.com"
  },
  {
    image: user_04,
    name: "cooper press",
    date: "Nov 14, 2023",
    amount: 100000,
    status: "refund",
    invoice: "www.filepath.com"
  },
  {
    image: user_05,
    name: "philip lubin",
    date: "Nov 13, 2023",
    amount: 74000,
    status: "paid",
    invoice: "www.filepath.com"
  },
  {
    image: user_06,
    name: "marcus bergson",
    date: "Nov 13, 2023",
    amount: 70000,
    status: "refund",
    invoice: "www.filepath.com"
  },
  {
    image: user_07,
    name: "jaydon vaccaro",
    date: "Nov 12, 2023",
    amount: 120000,
    status: "paid",
    invoice: "www.filepath.com"
  },
  {
    image: user_08,
    name: "corey schleifer",
    date: "Nov 12, 2023",
    amount: 77000,
    status: "refund",
    invoice: "www.filepath.com"
  },
  {
    image: user_09,
    name: "cooper press",
    date: "Nov 11, 2023",
    amount: 90000,
    status: "paid",
    invoice: "www.filepath.com"
  },
  {
    image: user_10,
    name: "philip lubin",
    date: "Nov 11, 2023",
    amount: 75000,
    status: "refund",
    invoice: "www.filepath.com"
  }
]

const format_amount = (amount) => {
  const add_comma = amount.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ",");
  return add_comma;
}

</script>

<template>
  <section class="table_data ml-[90px] overflow-hidden px-[20px] pt-[18px] border border-[#EDF2F7] bg-white w-[750px] h-[440px] rounded-[14px]">
    <h3 class="capitalize w-full font-[600] flex items-center mb-2 justify-between text-[18px]">
      <span>last orders</span>
      <span class="text-[#34caa5] cursor-pointer" @click="scroll = !scroll">{{ scroll ? 'show less' : 'see all' }}</span>
    </h3>

    <div class="order_table w-full overflow-y-hidden h-full" :class="{'overflow-y-scroll': scroll}">
      <table class="w-full text-left">
        <thead class="border-b border-[#EDF2F6]">
          <tr class="text-[#9CA4AB]">
            <th class="py-4 font-[400]">Name</th>
            <th class="py-4 font-[400]">Date</th>
            <th class="py-4 font-[400]">Amount</th>
            <th class="py-4 font-[400]">Status</th>
            <th class="py-4 font-[500]">Invoice</th>
          </tr>
        </thead>
        <tbody>
          <tr class="border-b border-[#EDF2F6]" v-for="(order, index) in orders" :key="index">
            <td class="py-4 capitalize flex item-center gap-2">
              <img class="w-8 h-8 rounded-full" :src="order.image" :alt="order.name">
              <span class="pt-[3px]">{{ order.name }}</span>
            </td>
            <td class="text-[#737373]">{{ order.date }}</td>
            <td class="font-[600]">${{ format_amount(order.amount) }}</td>
            <td class="capitalize"
              :class="{ 'text-[#34caa5]': order.status === 'paid', 'text-[#ED544E]': order.status === 'refund' }">{{
                order.status }}</td>
            <td>
              <a class="flex items-center gap-2 capitalize" :href="order.invoice" target="_blank">
                <img class="w-4 h-4" src="https://img.icons8.com/ios/50/document.png" alt="document" />
                <span class="text-[14px]">view</span>
              </a>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </section>
</template>

<style scoped>
.order_table::-webkit-scrollbar {
  width: 7px;
  /* padding: 5px */
}

/* Track */
.order_table::-webkit-scrollbar-track {
  box-shadow: inset 0 0 5px rgb(190, 190, 190);
  border-radius: 30px;
  margin: 10px;
}

/* Handle */
.order_table::-webkit-scrollbar-thumb {
  background: #7e7e7e;
  border-radius: 10px;
}


@media screen and (max-width: 1600px) {
  .table_data {
    margin-left: 40px;
    width: 630px !important;
    height: 420px;
  }
}

@media screen and (max-width: 1300px) {
  .table_data {
    margin-left: 0px;
    /* width: 600px !important; */
    width: 720px !important;
  }
  .table_data {
    margin-left: 0px;
  }
}

@media screen and (max-width: 800px) {
  .table_data {
    height: 380px;
    margin: 10px;
    padding-bottom: 40px;
  }
  .table_data h3 {
    font-size: 16px;
  }
  table {
    font-size: 13px;
  }
}
</style>
