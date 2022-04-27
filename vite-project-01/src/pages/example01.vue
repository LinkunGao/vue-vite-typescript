<template>
  <div>
    <div>example01</div>
    <div>
      <button @click="changeMsg">change</button>
      <div>{{ message }}</div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, Ref } from "vue";

let message: Ref<string> = ref("hello world");
const changeMsg = () => {
  message.value = "change the world";
};
</script>

<style lang="scss" scoped></style>
