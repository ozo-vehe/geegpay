<script setup>
import Barchat from './components/Barchat.vue';
import Market from './components/Market.vue';
import NavBar from './components/Navbar.vue';
import Platform from './components/Platform.vue';
import Sidebar from './components/Sidebar.vue';
import TableData from './components/TableData.vue';
</script>

<template>
  <main class="main_container bg-[#FAFAFA] pb-5">
    <NavBar />
    <Sidebar />
    <div class="dashboard_charts mb-10 flex flex-wrap justify-around gap-5">
      <Barchat />
      <Market />
    </div>
    <div class="dashboard_tables flex flex-wrap justify-around gap-5">
      <TableData />
      <Platform />
    </div>
  </main>
</template>

<style scoped>
@media screen and (max-width: 1600px) {
  .dashboard_charts,
  .dashboard_tables {
    justify-content: center;
  }
}

</style>
