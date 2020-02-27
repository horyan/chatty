<template>
  <div>
    <MessagesList :messageList="messages" />
    <input type="text" placeholder="Enter a message" v-model="newMessage" />
    <button @click="sendMessage(newMessage)">Send Message</button>
  </div>
</template>

<script>
import MessagesList from "./components/MessagesList";
import { db } from "./db";

export default {
  name: "App",
  components: {
    MessagesList
  },
  data() {
    return {
      messages: [],
      newMessage: ""
    };
  },
  firestore: {
    messages: db.collection("messages").orderBy("createdAt")
  },
  methods: {
    sendMessage(newMessage) {
      db.collection("messages").add({
        createdAt: new Date(),
        value: newMessage
      });
      this.newMessage = "";
    }
  }
};
</script>