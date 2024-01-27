<script setup>
import logo from '../assets/logo.png';
import calendar from '../assets/icons/calendar.png';
import notification_bell from '../assets/icons/bell.png';
import search from '../assets/icons/search.png';
import arrow_down from '../assets/icons/arrow-down.png';
import user_01 from '../assets/icons/user-01.png';
import { ref } from 'vue';

const show_menu = ref(false)

const showSidebar = () => {
  const sidebar = document.querySelector('.sidebar').style;
  sidebar.transform = 'translateX(0px)'
}
</script>

<template>
  <nav class="bg-[#FAFAFA] flex pl-[100px] flex-wrap items-center justify-between border py-[18px] pr-5 h-[80px]">
    <div class="nav_logo flex items-center gap-4">
      <img class="w-10 h-10 cursor-pointer" :src="logo" alt="Logo"  @click="showSidebar">
      <p class="capitalize text-[20px] font-[600]">dashboard</p>
    </div>

    <div class="nav_actions flex flex-wrap justify-between items-center gap-10 max-w-[950px]">
      <div
        class="nav_search_bar h-12 w-[350px] flex pl-4 items-center gap-8 border border-[#dadddd] bg-white rounded-[24px]">
        <img class="w-[18px] h-[18px]" :src="search" alt="Search icon">
        <input class="outline-none bg-inherit h-full" type="text" name="search" id="search" placeholder="Search...">
      </div>

      <div class="nav_calender flex items-center gap-x-3">
        <img class="w-5 h-5" :src="calendar" alt="Calender">
        <p class="text-[14px] capitalize">november 15, 2023</p>
      </div>

      <div class="nav_user_container flex items-center gap-x-12">
        <div class="nav_notification border p-2 rounded-full">
          <img class="w-5 h-5" :src="notification_bell" alt="Notification bell">
        </div>
        <div class="nav_user flex items-center gap-4">
          <img :src="user_01" alt="User image">
          <div class="nav_user_details_container flex items-center gap-4">
            <div class="nav_user_details">
              <p class="font-[400] inter">Justin Bergson</p>
              <p class="text-[14px] font-[400] text-[#787486] inter">justin@gmail.com</p>
            </div>
            <img class="w-6 h-6" :src="arrow_down" alt="Arrow down">
          </div>
        </div>
      </div>
    </div>

    <div class="hamburger_menu cursor-pointer relative">
      <img @click="show_menu = !show_menu" class="w-6 h-6" src="https://img.icons8.com/ios-filled/50/menu--v1.png"
        alt="menu--v1" />

      <div v-show="show_menu"
        class="drop_menu flex flex-col absolute top-[50px] rounded-[14px] py-6 px-4 right-0 z-10 bg-white w-[350px] border justify-between items-start gap-3">

        <div class="nav_user_container flex items-center justify-between border-b pb-2 w-full gap-2">
          <div class="nav_user flex items-center gap-4">
            <img :src="user_01" alt="User image">
            <div class="nav_user_details_container flex items-center gap-4">
              <div class="nav_user_details">
                <p class="font-[400] inter">Justin Bergson</p>
                <p class="text-[14px] font-[400] text-[#787486] inter">justin@gmail.com</p>
              </div>
              <img class="w-6 h-6" :src="arrow_down" alt="Arrow down">
            </div>
          </div>
          <div class="nav_notification border p-2 rounded-full">
            <img class="w-5 h-5" :src="notification_bell" alt="Notification bell">
          </div>
        </div>

        <div class="nav_calender flex items-center gap-x-3">
          <img class="w-5 h-5" :src="calendar" alt="Calender">
          <p class="text-[14px] capitalize">november 15, 2023</p>
        </div>

        <div
          class="nav_search_bar h-[45px] w-full flex pl-4 items-center gap-8 mt-4 border border-[#dadddd] bg-white rounded-[24px]">
          <img class="w-[18px] h-[18px]" src="https://img.icons8.com/ios/50/search--v1.png" alt="Search icon">
          <input class="bg-inherit outline-none h-full" type="text" name="search" id="search" placeholder="Search...">
        </div>
      </div>
    </div>
  </nav>
</template>

<style scoped>

.show_sidebar {
  transform: translateX(0px) !important;
}
.hamburger_menu {
  display: none;
}

.nav_logo img {
  display: none;
}

@media screen and (max-width: 1300px) {
  nav {
    padding: 0px 20px;
  }
  .nav_logo img {
    display: block;
  }
}

@media screen and (max-width: 1300px) {
  .hamburger_menu {
    display: block;
  }

  .nav_actions {
    display: none;
  }
}</style>
