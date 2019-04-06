<template>
  <div class="hello">
    <h1 :title="'hello' + titleMsg">{{ msg }}</h1>
    <div>
      <span v-html="number"></span>
      <button  v-text="text" @click="handleClick"></button>
    </div>
    <input type="text" v-model="inputValue">
    <p>{{inputValue}}</p>
  </div>
</template>

<script>
// 面向数据编程
// 事件绑定 v-click--@click
// 属性绑定 v-bind:---:
// 双向数据绑定 v-model
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Welcome to my first application',
      titleMsg: 'Welcome sherry',
      number: '<span>123</span>',
      text: 'test button',
      inputValue: ''
    }
  },
  methods: {
    handleClick: function () {
      this.number = '456'
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

</style>
