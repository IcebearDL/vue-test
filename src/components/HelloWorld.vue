<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
<!--    <h1 v-text="msg"></h1>-->
<!--    v-text 会覆盖原本内容，并产生闪烁，而插值表达式会闪烁-->

<!--    v-bind是绑定属性函数，v-bind中可以写js表达式-->

    <input type="text" v-model="num1">
    <select v-model="optionType">
      <option value="+">+加</option>
      <option value="-">-减</option>
      <option value="*">*乘</option>
      <option value="/">/除</option>
    </select>
    <input type="text" v-model="num2">
    <input type="button" value="计算的结果是=" v-on:click="getResult">
    <input type="text" v-model="countResult">

  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data() {
    return {
      msg: '一个简单的计算器',
      num1: null,
      num2: null,
      optionType: '+',
      countResult: null
    }
  },
  methods:{
    getResult(){
      if ((this.num1 === null) || (this.num2 === null)){
        alert('请输入需要计算的数字！')
      } else {
        switch (this.optionType) {
          case '+':
            this.countResult = Number(this.num1) + Number(this.num2);
            break;
          case '-':
            this.countResult = Number(this.num1) - Number(this.num2);
            break;
          case '*':
            this.countResult = Number(this.num1) * Number(this.num2);
            break;
          case '/':
            this.countResult = Number(this.num1) / Number(this.num2);
            break;
        }
      }
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
