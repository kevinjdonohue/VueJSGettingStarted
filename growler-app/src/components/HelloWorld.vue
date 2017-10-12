<template>
  <div class="hello">
    <!--Bind to a JS array of values - that refer to CSS classes-->
    <!-- <h1 v-once v-text="appName" v-bind:class="[accentColor, headers]"></h1> -->

    <!--Alternatively, bind to CSS classes directly via a boolean, turning them on or off-->
    <h1 v-once v-text="appName" v-bind:class="{
      'headers': true,
      'accent-color': isOnline
    }"></h1>
    <h2>Version: {{ appVersion }}</h2>
    <h2>Description: {{ appDescription }}</h2>
    <div v-html="appUrl"></div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      appName: 'Growler!',
      appVersion: '2.0.0',
      appDescription: 'My cool beer app!',
      appUrl: '<a href="http://www.growler.com">Growler</a>',
      // accentColor: 'accent-color',
      // headers: 'headers',
      isOnline: true
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}

.accent-color {
  color:#FF6A00
}

.headers {
  font-family: 'Verdana';
  font-size: 3em;
  margin: 0;
}
</style>
