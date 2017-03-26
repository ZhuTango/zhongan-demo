<template>
  <div id="app">
    <carousel></carousel>
    <block></block>
  </div>
</template>

<script>
import Hello from './components/Hello'
import Carousel from './components/Carousel'
import Block from './components/Block'

export default {
  name: 'app',
  components: {
    Hello,
    Carousel,
    Block
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
