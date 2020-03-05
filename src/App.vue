<template>
  <div class="flex mx-auto h-screen items-center w-1/2">
    <div class="border px-4 py-4 w-full">
      <MessagesList :messageList="messages"/>
      Your automatically generated chat name: {{name}}
      <div class="flex flex-wrap">
        <span v-if="!isValidMessage">Please enter valid message</span>
        <input class="flex-1 bg-white border border-blue-500 focus:outline-none focus:border-blue-700 py-2 px-4 appearance-none" type="text" placeholder="Enter a message" v-model="newMessage"/>
        <button class="bg-blue-500 border border-blue-500 hover:border-blue-700 hover:bg-blue-700 text-white font-bold py-2 px-4" @click="sendMessage(newMessage)">Send Message</button>
      </div>
    </div>
  </div>
</template>

<script>
import { name } from 'faker';
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
      newMessage: "",
      isValidMessage: true,
      name: ""
    };
  },
  firestore: {
    messages: db.collection("messages").orderBy("createdAt")
  },
  created() {
    this.name = name.findName();
  },
  methods: {
    sendMessage(message) {
      if (message === "") {
        this.isValidMessage = false;
        return
      }
      else {
        this.isValidMessage = true;
      }
      db.collection("messages").add({
        createdAt: new Date(),
        value: message,
        name: this.name
      });
      this.newMessage = "";
    }
  }
};
</script>