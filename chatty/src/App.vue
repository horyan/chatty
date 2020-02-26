<template>
  <div>
    <MessagesList :messageList="messages" />
    <input type="text" placeholder="Enter a message" v-model="newMessage">
    <button @click="sendMessage(newMessage)">Send Message</button>
  </div>
</template>

<script>
import MessagesList from "./components/MessagesList";

export default {
  name: 'App',
  components: {
    MessagesList
  },
  data() {
    return {
      messages: [],
      newMessage: ''
    }
  },
  methods: {
    sendMessage(newMessage) {
      this.messages = [...this.messages, newMessage];
      this.newMessage = '';
    }
  }
}
</script>