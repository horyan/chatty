<template>
  <div class="flex mx-auto h-screen items-center w-1/2">
    <div class="w-full">
      <MessagesList :messageList="messages"/>
      <div class="flex">
        <input class="flex-1 bg-white border border-blue-500 focus:outline-none focus:border-blue-700 py-2 px-4 appearance-none" type="text" placeholder="Enter a message" v-model="newMessage" />
        <button class="bg-blue-500 border border-blue-500 hover:border-blue-700 hover:bg-blue-700 text-white font-bold py-2 px-4" @click="sendMessage(newMessage)">Send Message</button>
      </div>
    </div>
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