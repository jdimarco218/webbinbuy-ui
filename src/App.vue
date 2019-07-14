<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/shotgunWojakSmall.png">
    <OrderEntry msg="Enter Symbol and Percentage to Buy and Sell!"/>
  </div>
</template>

<script>
import OrderEntry from './components/OrderEntry.vue'

export default {
  name: 'app',
  components: {
    OrderEntry
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #f8d870;
  background-image: url(https://cdn.streamelements.com/static/user/background_default.jpg);
  height: 100vh;
  margin: 0px;
}
body {
  margin: 0px;
}
</style>
