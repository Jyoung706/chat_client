<template>
  <div></div>
</template>

<script setup>
import { onMounted, ref } from "vue";
import socket from "../../server";
const user = ref("");

onMounted(() => {
  const data = prompt("이름을 입력해주세요");
  user.value = data;
  socket.emit("login", user.value, (res) => {
    console.log(res);
  });
});
</script>

<style></style>
