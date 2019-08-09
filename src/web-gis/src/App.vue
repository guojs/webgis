<template>
  <div id="app">
    
    <mapContainer msg="Welcome to Your Vue.js App" />
  </div>
</template>

<script>
import mapContainer from "./components/mapContainer.vue";

export default {
  name: "app",
  components: {
    mapContainer
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  padding:0;
  margin:0;
  width:100%;
  height:100%;
}
html,body{
   width:100%;
   height:100%;
}
</style>
