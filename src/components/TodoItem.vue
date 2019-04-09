<template>
  <li class="item" @click="handleClick">{{message}}</li>
</template>

<script>
export default {
  name: 'TodoItem',
	props: ['message', 'index'],
  methods: {
    handleClick: function () {
      // 子组件向父组件传递数据：发布订阅
      this.$emit('delete', this.index)
    }
	}
}
</script>
<style scoped>
  .item {
    color:red;
  }
</style>
