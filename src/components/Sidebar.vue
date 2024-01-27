<script setup>
import logo from '../assets/logo.png';
import dashboard from '../assets/icons/dashboard.png';
import dashboard_dark from '../assets/icons/dashboard_dark.svg';
import trend from '../assets/icons/trend.png';
import users from '../assets/icons/users.png';
import box from '../assets/icons/box.png';
import discount from '../assets/icons/discount.png';
import info from '../assets/icons/info.png';
import light_mode from '../assets/icons/light.svg';
import light_mode_active from '../assets/icons/light-active.svg';
import dark_mode from '../assets/icons/dark.svg';
import dark_mode_active from '../assets/icons/dark-active.svg';
import arrow_right from '../assets/icons/arrow-right.png';
import settings from '../assets/icons/settings.png';
import logout from '../assets/icons/logout.png';

import { ref } from 'vue';

const theme = ref('light');

const dark_bg = '#191826';
const light_bg = '';
const dark_text = '#161616';
const light_text = '#f7f7f7';
const light_border = 'thin solid #e2e8f0'

const upper_icons = ref([
  {
    url: dashboard,
    name: 'dashboard'
  },
  {
    url: trend,
    name: 'trend'
  },
  {
    url: users,
    name: 'users'
  },
  {
    url: box,
    name: 'box'
  },
  {
    url: discount,
    name: 'discount'
  },
  {
    url: info,
    name: 'Info'
  },
])

const lower_icons = [
  {
    url: arrow_right,
    name: 'arrow left'
  },
  {
    url: settings,
    name: 'settings'
  },
  {
    url: logout,
    name: 'Logout'
  },
]

const clickedIcon = ref('dashboard');

const activeIcon = (e) => clickedIcon.value = e.target.alt;

const hideSidebar = () => {
  if (window.innerWidth <= 1300) {
    const sidebar = document.querySelector('.sidebar').style;
    sidebar.transform = 'translateX(-100px)'
  }
}

window.addEventListener('resize', function () {
  if (window.innerWidth > 1300) {
    const sidebar = document.querySelector('.sidebar').style;
    sidebar.transform = 'translateX(0px)';
  } else {
    const sidebar = document.querySelector('.sidebar').style;
    sidebar.transform = 'translateX(-100px)';
  }
})

// Change the theme from light to dark and vice versa
const changeTheme = () => {
  // const ham_menu = document.querySelector('.drop_menu');
  // console.log(ham_menu);

  // Notification Dark Theme
  const nav = document.querySelector('nav');
  const calendar = nav.querySelectorAll('.nav_calender img');
  const search_bar = nav.querySelector('.nav_search_bar');
  const search_img = search_bar.querySelectorAll('img')
  const notification = nav.querySelector('.nav_notification img');

  // Sidebar Dark Theme
  const sidebar = document.querySelector('.sidebar');
  const theme_container = sidebar.querySelector('.theme_container');
  upper_icons.value[0].url = dashboard_dark;

  // Main container
  const main = document.querySelector('.main_container');

  // Barchart
  const barchart = main.querySelector('.barchart');
  const select = barchart.querySelector('.sort_selection');

  // Market Cards
  const market_cards = main.querySelectorAll('.dashboard_card');

  // Table
  const table = main.querySelector('.table_data');
  const thead = table.querySelector('thead');
  const tbody = table.querySelectorAll('tbody tr');

  // Platform
  const platform = main.querySelector('.platform');
  const price_percentage = platform.querySelectorAll('.price_percentage p');

  // Nav menu
  const nav_menu = main.querySelector('.drop_menu');
  const menu_search = nav_menu.querySelector('.nav_search_bar');
  const menu_search_img = menu_search.querySelectorAll('img');
  const notif = nav_menu.querySelector('.nav_notification img');

  if (theme.value === 'light') {
    theme.value = 'dark';
    // Nav menu
    nav_menu.style.backgroundColor = dark_bg;
    nav_menu.style.border = '2px solid #000';
    menu_search.style.backgroundColor = dark_bg;
    menu_search.style.border = '2px solid #000';
    notification.setAttribute('src', 'https://img.icons8.com/ios/ffffff/50/appointment-reminders--v1.png')
    menu_search_img.forEach((img) => {
      img.setAttribute('src', 'https://img.icons8.com/ios/ffffff/50/search--v1.png')
    })

    // Nav
    nav.style.backgroundColor = dark_bg;
    nav.style.borderColor = '#292929';
    nav.style.color = light_text;
    notif.setAttribute('src', 'https://img.icons8.com/ios/ffffff/50/appointment-reminders--v1.png')
    search_bar.style.backgroundColor = dark_bg;
    search_bar.style.border = '2px solid #000';

    calendar.forEach((cal) => {
      cal.setAttribute('src', 'https://img.icons8.com/ios/ffffff/50/calendar--v1.png')
    })
    search_img.forEach((img) => {
      img.setAttribute('src', 'https://img.icons8.com/ios/ffffff/50/search--v1.png')
    })

    // Sidebar
    sidebar.style.backgroundColor = dark_bg;
    theme_container.style.backgroundColor = '#292929';

    // Main
    main.style.backgroundColor = dark_bg;

    // Barchart
    barchart.style.backgroundColor = dark_bg;
    barchart.style.border = '2px solid #000';
    barchart.style.color = light_text;

    select.style.backgroundColor = dark_bg;
    select.style.border = '2px solid #000';
    select.style.color = light_text;

    // Market Cards
    market_cards.forEach((card) => {
      card.style.backgroundColor = dark_bg;
      card.style.color = light_text;
      card.style.border = '2px solid #000';
      const card_details = card.querySelector('.card_details p');
      card_details.style.color = '#f7f7f7'
    })

    // Tables
    table.style.backgroundColor = dark_bg;
    table.style.border = '2px solid #000';
    table.style.color = light_text;
    thead.style.borderBottom = '2px solid #000';
    tbody.forEach((tr) => {
      tr.style.borderBottom = '2px solid #000';
    })

    // Platform
    platform.style.backgroundColor = dark_bg;
    platform.style.color = light_text;
    platform.style.border = '2px solid #000';
    price_percentage.forEach((p) => {
      p.style.color = '#afafaf';
    })

  } else if (theme.value === 'dark') {
    theme.value = 'light';

    // Nav menu
    nav_menu.style.backgroundColor = '#fff';
    nav_menu.style.border = light_border;
    menu_search.style.backgroundColor = '#fff';
    menu_search.style.border = light_border;
    notif.setAttribute('src', 'https://img.icons8.com/ios/50/appointment-reminders--v1.png')
    menu_search_img.forEach((img) => {
      img.setAttribute('src', 'https://img.icons8.com/ios/50/search--v1.png')
    })

    nav.style.backgroundColor = light_bg;
    nav.style.color = dark_text;
    nav.style.borderColor = '#e2e8f0';
    notification.setAttribute('src', 'https://img.icons8.com/ios/50/appointment-reminders--v1.png')
    search_bar.style.backgroundColor = light_bg;
    search_bar.style.border = light_border;

    calendar.forEach((cal) => {
      cal.setAttribute('src', 'https://img.icons8.com/ios/50/calendar--v1.png')
    })

    search_img.forEach((img) => {
      img.setAttribute('src', 'https://img.icons8.com/ios/50/search--v1.png')
    })

    // Sidebar
    sidebar.style.backgroundColor = '#F7F8FA'
    theme_container.style.backgroundColor = '#fff';
    upper_icons.value[0].url = dashboard;

    // Main
    main.style.backgroundColor = light_bg;

    // Barchart
    barchart.style.backgroundColor = '#fff';
    barchart.style.border = light_border;
    barchart.style.color = dark_text;

    select.style.backgroundColor = '#fff';
    select.style.border = light_border;
    select.style.color = dark_text;

    // Market Cards
    market_cards.forEach((card) => {
      card.style.backgroundColor = '#fff';
      card.style.color = dark_text;
      card.style.border = light_border;
      const card_details = card.querySelector('.card_details p');
      card_details.style.color = dark_text
    })

    // Tables
    table.style.backgroundColor = '#fff';
    table.style.border = light_border;
    table.style.color = dark_text;
    thead.style.borderBottom = 'thin solid #EDF2F6';
    tbody.forEach((tr) => {
      tr.style.borderBottom = 'thin solid #EDF2F6';
    })

    // Platform
    platform.style.backgroundColor = '#fff';
    platform.style.color = dark_text;
    platform.style.border = light_border;
    price_percentage.forEach((p) => {
      p.style.color = '#525252';
    })

  }
}
</script>

<template>
  <section
    class="sidebar fixed top-0 bg-[#F7F8FA] min-h-screen w-20 flex flex-wrap items-between justify-center pt-5 pb-5">
    <div class="sidebar_upper_icons w-full flex flex-col justify-between items-between min-h-[700px]">
      <div class="upper_icons flex flex-col items-center gap-6">
        <img @click="hideSidebar" class="cursor-pointer w-10 h-10" :src="logo" alt="Logo">

        <div class="w-full flex relative justify-center icons" v-for="(icon, index) in upper_icons" :key="index">
          <img class="cursor-pointer" :src="icon.url" :alt="icon.name">
          <svg v-if="clickedIcon === icon.name" class="absolute right-0 top-[50%] -translate-y-[50%]"
            xmlns="http://www.w3.org/2000/svg" width="3" height="21" viewBox="0 0 3 21" fill="none">
            <path
              d="M6.53467e-06 3.02509C7.11773e-06 1.42129 1.40951 0.182713 3 0.388889V21C1.34315 21 4.88293e-07 19.6569 1.09063e-06 18L6.53467e-06 3.02509Z"
              fill="#0D062D" />
          </svg>
        </div>

        <div class="theme_container relative flex flex-col gap-8 items-center rounded-[100px] bg-white p-3">
          <div class="relative z-10 light_mode p-2 rounded-full cursor-pointer" @click="changeTheme">
            <img v-if="theme === 'dark'" class="w-6 h-6" :src="light_mode" alt="Light mode">
            <img v-if="theme === 'light'" class="w-6 h-6 rounded-full" :src="light_mode_active" alt="Active light mode">
          </div>

          <div class="relative z-10 dark_mode p-2 rounded-full cursor-pointer" @click="changeTheme">
            <img v-if="theme === 'light'" class="w-6 h-6" :src="dark_mode" alt="Dark mode">
            <img v-if="theme === 'dark'" class="w-6 h-6" :src="dark_mode_active" alt="Active dark mode">
          </div>

          <div
            class="absolute top-[9px] w-[45px] h-[45px] rounded-full bg-[#34caa5] theme_indicator transition-all duration-500"
            :class="{ 'translate-y-[160%]': theme === 'dark', 'top-[9px]': theme === 'light' }">

          </div>
        </div>
      </div>

      <div class="lower_icons flex flex-col items-center gap-6">
        <div class="w-full flex relative justify-center icons" v-for="(icon, index) in lower_icons" :key="index">
          <img class="cursor-pointer" @click="activeIcon" :src="icon.url" :alt="icon.name">
          <svg v-if="clickedIcon === icon.name" class="absolute right-0 top-[50%] -translate-y-[50%]"
            xmlns="http://www.w3.org/2000/svg" width="3" height="21" viewBox="0 0 3 21" fill="none">
            <path
              d="M6.53467e-06 3.02509C7.11773e-06 1.42129 1.40951 0.182713 3 0.388889V21C1.34315 21 4.88293e-07 19.6569 1.09063e-06 18L6.53467e-06 3.02509Z"
              fill="#0D062D" />
          </svg>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
@media screen and (max-width: 1300px) {
  .sidebar {
    transform: translateX(-100px);
    transition: 0.3s all;
    z-index: 10;
    color: #e2e8f0;
  }
}

@media screen and (min-width: 1301px) {
  .sidebar {
    transform: translateX(0px);
    transition: 0.3s all;
    z-index: 10;
  }
}
</style>
