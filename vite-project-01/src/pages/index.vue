<template>
  <div>
    <button @click="goRouter">example01</button>
  </div>
</template>

<script setup lang="ts">
import { ref } from "vue";
import { useRouter } from "vue-router";

const router = useRouter();

const goRouter = () => {
  console.log(router);
  router.push("/example01");
};
</script>

<style scoped></style>
