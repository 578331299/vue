<template>
  <div class="text">
    <textarea ref="text" v-model="currentInputValue"></textarea>
    <div class="buttonGroup">
       <button class="button" @click="sendMessage" :disabled="currentInputValue ===''">
    	  发送信息
        </button>
       <button class="button" @click="receiveMessage" :disabled="currentInputValue ===''">
    	  接受信息
      </button>
    </div>
   
  </div>
</template>

<script>
export default {
  name: 'InputText',
  props: ['inputValue'],
  data() {
    return {
      currentInputValue: this.inputValue
    }
  },
  methods: {
    sendMessage: function () {
      this.$emit('send', this.currentInputValue, true)
      this.currentInputValue = ''
    },
    receiveMessage: function () {
      this.$emit('send', this.currentInputValue, false)
      this.currentInputValue = ''
    }
	}
}
</script>

<style scoped>
.text {
  top:85%;
  height:15%;
  width:100%;
  background-color:#fff;
  position:absolute;
  border:1px solid #ddd;
}
textarea {
  box-sizing: border-box;
  height: 60px;
  width: 100%;
  border: none;
}
.buttonGroup {
  position: absolute;
  right: 5px;
  width:160px;
  height: 28px;
  bottom:15px
}
.button {
  width: 75px;
  height: 28px;
  line-height: 28px;
  box-sizing: border-box;
  text-align: center;
  border: 1px solid #ddd;
  border-radius: 3px;
  background-color:green;
}

</style>
