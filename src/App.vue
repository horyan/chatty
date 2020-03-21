<template>
  <div>
    <div class="mt-24">
      <img class="mx-auto h-48" src="./assets/logo.png">
    </div>
    <section class="pt-12 pb-24 px-4">
      <div class="max-w-3xl mx-auto">
        <MessagesList class="my-2" :messageList="messages" :activeUser="name"/>
        <span v-if="!isValidMessage" class="flex text-blue-600 text-sm">Please enter valid message</span>
        <div class="flex leading-snug">
          <input class="flex-grow rounded-l bg-gray-200 border border-gray-200 hover:border-gray-500 focus:bg-white focus:border-gray-500 focus:outline-none text-gray-700 px-3 py-2"
          type="text"
          placeholder="Enter message..."
          v-on:keyup.enter="sendMessage(newMessage)"
          v-model="newMessage"/>
          <button class="rounded-r bg-blue-600 border border-blue-600 hover:border-blue-700 hover:bg-blue-700 focus:outline-none text-white px-8 py-3" @click="sendMessage(newMessage)">Send</button>
        </div>
        <span class="flex text-sm py-1">Your automatically generated chat name:
        <span class="font-semibold text-blue-600 text-sm pl-1">{{name}}</span>
        </span>
      </div>
    </section>
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
