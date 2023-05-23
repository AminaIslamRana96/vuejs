/* eslint-disable */ 
<template>
  <div class="main-page">
    <HeaderH />
    <div class="main">
      <SideBar />
      <ColumnSide />
      </div>
      <div class="cam">
      <cameraC />
      <NewTab />
    </div>
  </div>
</template>

<script>
import HeaderH from "./components/HeaderH.vue";
import SideBar from "./components/SideBar.vue"
import ColumnSide from "./components/ColumnSide.vue";
import cameraC from "./components/cameraC.vue";
import NewTab from "./components/NewTab.vue"
export default {
  name: "App",
  components: {
    HeaderH,
    SideBar,
    ColumnSide,
    cameraC,
    NewTab
  },
};
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}



.main {
  display: flex;
}
</style>
