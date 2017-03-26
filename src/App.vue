<template>
  <div id="app">
    <carousel :mockimgs="{mockimgs}"></carousel>
    <block :mockmsgs="{mockmsgs}"></block>
  </div>
</template>

<script>
import Carousel from './components/Carousel'
import Block from './components/Block'
import Mock from './assets/mock.json'
export default {
  name: 'app',
  components: {
    Carousel,
    Block
  },
  data () {
    return {
      mockimgs: Mock.imgs,
      mockmsgs: Mock.msgs
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
}
</style>
