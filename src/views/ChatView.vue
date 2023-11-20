<template>
  <div>
    <ChatList :messageList="messageList" />
  </div>
</template>

<script setup>
import ChatList from "../components/ChatList.vue";
import { onMounted, ref } from "vue";
import socket from "../../server";
const user = ref("");
const newMessage = ref("");
const messageList = ref([]);

onMounted(() => {
  const data = prompt("이름을 입력해주세요");
  user.value = data;
  socket.emit("login", user.value, (res) => {
    console.log(res);
  });
  socket.on("message", (res) => {
    console.log(res);
    messageList.value.push(res.chat);
  });
});
</script>

<style></style>
