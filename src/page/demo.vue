<template>
  <div class="chat-content">
    <div class="chatRoom">
			<message-list :message="mesList" :userInfo="user"></message-list>
			<input-text @send="handleSend"></input-text>
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
        { content: '你好', date: new Date(), self: true },
        { content: '可以发送信息哦', date: new Date(), self:false }
      ]
    }
  },
  methods: {
    handleSend: function (message, self) {
      const content = {content: message, date: new Date(), self };
      this.mesList.push(content);
      this.inputMessage = '';
    }
  }
}
</script>
<style scoped>
  .chat-content {
    width:450px;
    height:500px;
    background-color:#ddd;
    margin:0 auto;
   
  }
  .chatRoom {
   position:relative;
   height:100%;
  }
</style>

