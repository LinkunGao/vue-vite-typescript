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
import { customRef } from "vue";

function myRef<T>(value: T) {
  return customRef((track, trigger) => {
    return {
      get() {
        track();
        return value;
      },
      set(newVal: T) {
        console.log("set value");
        value = newVal;
        trigger();
      },
    };
  });
}

let message = myRef<string>("hello world!");
const changeMsg = () => {
  message.value = "change the world!!!";
};
</script>

<style lang="scss" scoped></style>
