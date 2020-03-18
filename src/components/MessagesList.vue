<template>
  <ul>
    <li v-for="(message, index) in messageList" :key="index" class="flex justify-between my-1" v-show="message.value">
      <div>
        <span v-if="message.name" class="font-semibold px-2 text-sm text-white rounded-full"
        :class="{'bg-blue-600': activeUser !== message.name, 'bg-orange-500': activeUser === message.name}"
        >{{message.name}}</span>
        <span class="pl-2">{{message.value}}</span>
      </div>
      <span class="text-gray-500">{{getRelativeTime(message.createdAt)}}</span>
    </li>
  </ul>
</template>

<script>
import * as moment from "moment";
export default {
  props: ["messageList", "activeUser"],
  methods: {
    getRelativeTime(timestamp) {
    return moment(timestamp.toDate(), "YYYYMMDD").fromNow();
    }
  }
};
</script>