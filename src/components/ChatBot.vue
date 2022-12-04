<template>
  <div>
    <div id="header">
      <img alt="Vue logo" src="../assets/lab_logo.png">
      <div class="input-container">
        <input v-model="newMessageText" placeholder="Type your message here..." @keyup.enter="sendMessage" />
        <button @click="sendMessage" style="margin-left: 10px;">Send</button>
      </div>
    </div>
    <div class="chat-window">
      <div class="message-container" ref="messageContainer">
        <div class="message" v-for="message in messages" v-bind:key="message.id">
          <div v-if="message.type === 'user'" class="bubble-user fade-in">
            <p>{{ message.text }}</p>
          </div>
          <div v-else class="bubble-bot fade-in">
            <p>{{ message.text }}</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style src="../styles/chat-bot.css">

</style>

<script>
export default {
  data: function () {
    return {
      messages: [],
      newMessageText: ''
    }
  },
  mounted() {
    this.updateMessageContainerSize();
    window.addEventListener('resize', this.updateMessageContainerSize);
  },
  beforeUnmount() {
    window.removeEventListener('resize', this.onResize);
  },
  methods: {
    updateMessageContainerSize: function () {
      const { innerWidth, innerHeight } = window;
      this.$refs.messageContainer.style.width = `${innerWidth}px`;
      this.$refs.messageContainer.style.height = `${innerHeight}px`;
    },
    sendMessage: function () {
      // メッセージを配列に追加する
      this.messages.push({
        type: 'user',
        text: this.newMessageText
      });

      // チャットボットからの返信を受け取る
      this.receiveMessage();

      // メッセージをクリアする
      this.newMessageText = '';
      // メッセージが追加されたら「messageContainer」要素にスクロールする
      this.$nextTick(() => {
        this.$refs.messageContainer.scrollTop = this.$refs.messageContainer.scrollHeight;
      });
    },
    receiveMessage: function () {
      // チャットボットからの返信を処理する
      let responseText = '';
      if (this.newMessageText.toLowerCase() === 'hello') {
        responseText = 'Hi there!';
      } else if (this.newMessageText.toLowerCase() === 'how are you?') {
        responseText = "I'm doing great, thank you for asking!";
      } else {
        responseText = "I'm sorry, I don't understand what you mean.";
      }
      // チャットボットからの返信を配列に追加する
      this.messages.push({
        type: 'bot',
        text: responseText
      });
      // メッセージが追加されたら「messageContainer」要素にスクロールする
      this.$nextTick(() => {
        this.$refs.messageContainer.scrollTop = this.$refs.messageContainer.scrollHeight;
      });
    }
  }
};
</script>
