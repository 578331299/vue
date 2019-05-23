<template>
  <div class="chat-content">
    <div class="userInfo">
      <img class="image" :src="user[1].img" />
      <div class="username">{{user[1].name}}</div>
    </div>
    <div class="chatRoom">
			<message-list :message="mesList" :userInfo="user"></message-list>
			<input-text @send="handleSend" :inputValue="inputMessage"></input-text>
    </div>
  </div>
</template>
<script>


import MessageList from '@/components/MessageList'
import InputText from '@/components/InputText'
export default {
  name: 'Demo',
	components: {
    'message-list': MessageList,
		'input-text': InputText
  },
  data () {
    return {
      user: [
        { id: 0, name: 'sherry', img:'../static/sherry.png' },
        { id: 1, name: '机器人', img:'../static/jiqiren.png' },
      ],
      mesList: [
        { content: '我这里有一个网站你可以去看看哦https://github.com/578331299/vue-demo', date: new Date(), self: true },
        { content: '可以发送带有http或https开头的url哦', date: new Date(), self:false }
      ],
      inputMessage: ''
    }
  },
  methods: {
    handleSend: function (message, self) {
      const content = {content: message, date: new Date(), self }
      this.mesList.push(content)
    }
  }
}
</script>
<style scoped>
  .image{
    width:36px;
    height:36px;
    float:left;
  }
  .username {
    float:left;
    font-size:12px;
    padding: 12px;
  }
  .chat-content {
    width:450px;
    height:500px;
    background-color:#ddd;
    margin:0 auto;
   
  }
  .userInfo {
    height:10%;
    background-color:#fff;
    border-bottom:1px solid #5a5a5a;
  }
  .chatRoom {
   position:relative;
   height:90%;
  }
</style>

