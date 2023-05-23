<template>

  <div>
  
  <p v-if="isNewTabNotificationVisible">New tab opened!</p>
  
  <!-- Your component content -->
  
  </div>
  
  </template>
  
  <script>
  
  export default {
  
  data() {
  
  return {
  
  isNewTabNotificationVisible: false
  
  };
  
  },
  
  mounted() {
  
  window.onfocus = () => {
  
  this.isNewTabNotificationVisible = false;
  
  };
  
  window.onblur = () => {
  
  this.isNewTabNotificationVisible = true;
  alert("You change the tab.");
  
  };
  
  }
  
  };
  
  </script>