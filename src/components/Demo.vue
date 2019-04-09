<template>
  <div>
    <h1 :title="'hello' + titleMsg">{{ msg }}</h1>
    <div class="test_div">
      <span v-html="number" v-if="show"></span>
      <button  class="button" v-text="text" @click="handleClick"></button>
    </div>
    姓：<input type="text" v-model="firstName">
    名: <input type="text" v-model="lastName">
    <p>{{fullName}}</p>
    <div>{{count}}</div>
    <ul>
      <li v-for="item of list" :key="item">{{item}}</li>
    </ul>
  </div>
</template>
<script>
// 面向数据编程
// 事件绑定 v-click--@click
// 属性绑定 v-bind:---:
// 双向数据绑定 v-model
// 指令 v-if,v-show, v-for

// 全局组件(动态传值message),组件也是实例，父组件向子组件传值：属性传值
// 父组件接收方法 @delete
// import Vue from 'vue'
// Vue.component('todo-item', {
//   props: ['message', 'index'],
//   template: '<li @click="handleClick">{{message}}</li>',
//   methods: {
//     handleClick: function () {
//       // 子组件向父组件传递数据：发布订阅
//       this.$emit('delete', this.index)
//     }
//   }
// })
export default {
  name: 'Demo',
  data () {
    return {
      msg: 'Welcome to my first application',
      titleMsg: 'Welcome sherry',
      number: '<span>123</span>',
      text: 'test if',
      firstName: '',
      lastName: '',
      count: 0,
      show: true,
      list: ['react', 'angular', 'vue']
    }
  },
  methods: {
    handleClick: function () {
      this.number = '456'
      this.show = !this.show
    }
  },
  // 计算属性 computed
  computed: {
    fullName: function () {
      return this.firstName + ' ' + this.lastName
    }
  },
  // 侦听器watch
  watch: {
    fullName: function () {
      this.count++
    }
  }
}
</script>
<style scoped>
  .test_div{
    margin-bottom:50px;
  }
  .button{
    width:100px;
    height:25px;
  }
</style>

