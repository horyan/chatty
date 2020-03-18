<template>
  <div class="flex mx-auto h-screen items-center w-1/2">
    <div class="w-full">
      <MessagesList class="my-2" :messageList="messages"/>
      <span v-if="!isValidMessage" class="flex text-blue-600">Please enter valid message</span>
      <span class="flex border-t border-gray-500 py-1">Your automatically generated chat name:
        <span class="font-semibold text-blue-600 pl-1">{{name}}</span>
      </span>
      <div class="flex leading-snug">
        <input class="flex-1 rounded-l bg-gray-200 border border-gray-200 hover:border-gray-500 focus:bg-white focus:border-gray-500 focus:outline-none text-gray-700 px-3 py-2" type="text" placeholder="Enter message..." v-model="newMessage"/>
        <button class="rounded-r bg-blue-600 border border-blue-600 hover:border-blue-700 hover:bg-blue-700 focus:outline-none text-white px-8 py-3" @click="sendMessage(newMessage)">Send</button>
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