<template>
  <div class="message">
    <div class="msg-left">
      <img v-bind:src="msg.url" alt="">
    </div>
    <div class="msg-right">
      <div class="msg-title" v-text="msg.name"></div>
      <p class="msg-content" v-bind:class="{fold: foldState}" v-text="msg.contetnt"></p>
      <div class="msg-btn" v-on:click="fold()">
        <span v-if="foldState">展开</span>
        <span v-if="!foldState">收起</span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'hello',
  props: ['mockmsg'],
  data () {
    return {
      foldState: false,
      msg: this.mockmsg.mockmsg
    }
  },
  mounted: function () {
    console.log(this.msg)
  },
  methods: {
    fold () {
      this.foldState = !this.foldState
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
  .message{
    // height: 100%;
    display: flex;
    margin: 3px 20px;
    border-bottom: 1px solid #dcdcdc;
    padding: 20px 0;
    .msg-left{
      display: flex;
      flex: 1;
      border-right: 2px solid #dcdcdc;
      justify-content: center;
      align-items: center;
      img {
        height: 50px;
        width: 50px;
      }
    }
    .msg-right{
      flex: 5;
      padding-left: 20px;
      overflow: hidden;
      .msg-title{
        font-size: 20px;
        color: black;
      }
      .msg-content{
        overflow: hidden;
        word-wrap:break-word;
        text-align: left;
        margin: 10px;
      }
      .fold{
        display:block;
        white-space:nowrap; 
        overflow:hidden; 
        text-overflow:ellipsis;
        height: 20px;
      }
      .msg-btn{
        float: right;
        display: flex;
        justify-content: center;
        align-items: center;
        margin-right: 20px;
        font-size: 11px;
        background-color: #f2f2f2;
        width: 40px;
        height: 20px;
        border: 1px solid #dcdcdc;
        border-radius: 3px;
        cursor: pointer;
      }
      .msg-btn:hover,
      .msg-btn:focus {
        background-color: #dcdcdc;
      }
    }
  }
</style>
