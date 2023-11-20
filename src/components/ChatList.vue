<template>
  <div>
    <div>
      <span>채팅창</span>
      <ul>
        <li v-for="(msg, index) in messageList" :key="index">{{ msg }}</li>
      </ul>
    </div>
    <form @submit="sendMessage">
      <input type="text" v-model="msg" />
      <button type="submit">전송</button>
    </form>
  </div>
</template>

<script setup>
import { ref, watch } from "vue";
import socket from "../../server";

const msg = ref("");

const { messageList } = defineProps(["messageList"]);

const sendMessage = (e) => {
  e.preventDefault();
  socket.emit("sendMessage", msg.value, (res) => {
    console.log(res);
  });
};
</script>

<style></style>
