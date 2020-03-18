<template>
  <div class="flex mx-auto h-screen items-center w-1/2">
    <div class="w-full">
      <MessagesList class="my-5" :messageList="messages"/>
      <span v-if="!isValidMessage" class="flex text-blue-300">Please enter valid message</span>
      <span class="flex border-t border-blue-500 py-1">Your automatically generated chat name:
        <span class="font-semibold text-blue-500 pl-1">{{name}}</span>
      </span>
      <div class="flex">
        <input class="flex-grow rounded-l-lg bg-gray-100 border border-blue-500 focus:outline-none focus:border-blue-700 py-2 px-4 appearance-none" type="text" placeholder="Enter a message" v-model="newMessage"/>
        <button class="rounded-r-lg bg-blue-500 border border-blue-500 hover:border-blue-700 hover:bg-blue-700 text-white font-bold py-2 px-4" @click="sendMessage(newMessage)">Send Message</button>
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