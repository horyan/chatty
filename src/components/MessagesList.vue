<template>
  <ul>
    <li v-for="(message, index) in messageList" :key="index" class="flex justify-between my-1" v-show="message.value">
      <div>
        <span v-if="message.name" class="font-semibold px-2 bg-blue-600 text-white rounded-full">{{message.name}}</span>
        <span class="pl-2">{{message.value}}</span>
      </div>
      <span class="text-gray-500">{{message.createdAt}}</span>
    </li>
  </ul>
</template>

<script>
export default {
  props: ["messageList"]
};
</script>