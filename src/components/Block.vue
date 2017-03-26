<template>
  <div class="block">
    <template v-for="mockmsg in msgs">
      <message :mockmsg='{mockmsg}'></message>
    </template>
  </div>
</template>

<script>
import $ from 'jquery'
import Message from './Message'
let win = window

export default {
  components: {
    Message
  },
  props: ['mockmsgs'],
  data () {
    return {
      msgs: this.mockmsgs.mockmsgs
    }
  },
  mounted: function () {
    let self = this
    self.changeHeight()
    $(win).resize(function () {
      self.changeHeight()
    })
  },
  methods: {
    changeHeight () {
      let $block = $('.block')
      let $carousel = $('.carousel')
      let blockHeight = $(window).height() - $carousel.height() - 25
      $block.height(blockHeight)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
  .block{
    margin-top: 5px;
    overflow: auto;
  }
</style>
