<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <div v-html="msg2"></div>
<!--    <h1 v-text="msg"></h1>-->
<!--    v-text 会覆盖原本内容，并产生闪烁，而插值表达式会闪烁-->

<!--    v-bind是绑定属性函数，v-bind中可以写js表达式-->
    <input type="button" value="浪起来" @click="moveWords">
    <input type="button" value="别浪" @click="stopMoveWords">
    <div>{{ msg3 }}</div>

  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data() {
    return {
      msg: 'Welcome to Your Vue.js App',
      msg2: '<h2>你好我是h2</h2>',
      msg3: '猥琐发育，别浪~~!',
      intervalId: null
    }
  },
  methods:{
    moveWords() {
      if(this.intervalId === null){
        this.intervalId = setInterval(() => {
          this.msg3 = this.msg3.substring(1) + this.msg3.substring(0,1);
        },100)
      }
    },
    stopMoveWords() {
      clearInterval(this.intervalId);
      this.intervalId =null;
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
  color: black!important;
}
</style>
