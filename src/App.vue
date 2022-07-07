<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
    <component v-if="componentName" :is="componentName"/>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import Vue from 'vue'

export default {
  name: 'App',
  components: {
    HelloWorld
  },
  data() {
    return {
      componentName: ''
    }
  },
  mounted() {
    const name = ['test1', 'test2'][Math.round(Math.random())];
    console.log(name)
    import(`./components/${name}/index.vue`).then((module) => {
      Vue.component('my-component-name', module.default)
      this.componentName = 'my-component-name'
    })
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
