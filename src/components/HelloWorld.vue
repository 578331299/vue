<template>
  <div class="hello">
    <demo-list></demo-list>
    <h1>toollist demo</h1>
    <input type="text" v-model="inputValue">
    <button @click="handleSubmit">提交</button>
    <ul>
      <todo-item
        v-for="(item, index) of fullList"
        :key="index"
        :message="item"
        :index="index"
        @delete="hadleDelete"></todo-item>
    </ul>
  </div>
</template>

<script>
import TodoItem from '@/components/TodoItem'
import Demo from '@/components/Demo'
export default {
  name: 'HelloWorld',
  components: {
    'todo-item': TodoItem,
    'demo-list': Demo
  },
  data () {
    return {
      inputValue: '',
      fullList: []
    }
  },
  methods: {
    handleSubmit: function () {
      this.fullList.push(this.inputValue)
      this.inputValue = ''
    },
    hadleDelete: function (index) {
      this.fullList.splice(index, 1)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
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
