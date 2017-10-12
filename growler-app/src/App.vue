<template>
  <div id="app">
    <img style="height: 300px;" src="./assets/growler-logo.jpg">
    <!--TODO:  Figure out how to v-bind the relative path the image to the src attribute of the img tag-->
    <!-- <img alt="Growler" v-bind:src="appLogo" style="height:300px;" /> -->
    <router-view/>
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      // TODO:  Not being used yet; need to figure out how to v-bind this value the the src of the img tag (above)
      appLogo: './assets/growler-logo.jpg'
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
