<template>
  <div class="carousel">
    <div class="cau-imgs">
      <template v-for="img in imgs">
        <img v-bind:src="img.url"  alt="" v-bind:class="{ show: img.selected, hide: !img.selected }">
      </template>
    </div>
    <div class="cau-dots">
      <template v-for="(img, index) in imgs">
        <span class="cau-dot" v-bind:class="{ selected: img.selected}" v-on:click="clkChangeImg(index)"></span>
      </template>
    </div>
  </div>
</template>

<script>
import Mock from '../assets/img-mock.json'
let win = window
export default {
  name: 'hello',
  data () {
    return {
      imgs: Mock.imgs,
      num: 0,
      ti: null
    }
  },
  mounted: function () {
    console.log(this.imgs)
    this.run(0)
  },
  methods: {
    run (num) {
      console.log('run')
      let self = this
      self.num = !isNaN(num) ? num : self.num
      self.changeImg(self.num)
      self.ti = setInterval(function () {
        // console.log(self.num)
        self.num = self.num + 1 < self.imgs.length ? self.num + 1 : 0
        self.changeImg(self.num)
      }, 2000)
    },
    changeImg (num) {
      console.log('change img')
      for (let i = 0; i < this.imgs.length; i++) {
        if (i === num) {
          this.imgs[i].selected = true
          // console.log(1)
        } else {
          this.imgs[i].selected = false
          // console.log(2)
        }
      }
    },
    clkChangeImg (num) {
      console.log(num)
      win.clearInterval(this.ti)
      this.run(num)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.carousel{
  height: 300px;
  overflow: hidden; 
  .cau-imgs{
    width: 100%;
    img{
      width: 100%;
      height: 300px;
    }
    .show{
      display: block;
    }
    .hide{
      display: none;
      height: 0px;
    }
  }
  .cau-dots{
    position: relative;
    // left: 50%;
    top: -20px;
    margin: 0 auto;
    bottom: 20px;
    z-index: 200;
    height: 10px;
    width: 100px;
    .cau-dot{
      float: left;
      margin-right: 5px;
      width: 10px;
      height: 10px;
      border: 1px solid #fff;
      border-radius: 50%;
      background: #333;
      cursor: pointer;
    }
    .selected{
      background-color: orangered;
    }
  }
}
</style>
