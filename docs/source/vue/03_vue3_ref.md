# Ref family

## Ref

接受一个内部值并返回一个响应式且可变的 ref 对象。ref 对象仅有一个 .value property，指向该内部值。

In below situation we cannot change the `messeage` value, because variable message is not a responsive variable.

```html
<template>
  <div>
    <div>
      <button @click="changeMsg">change</button>
      <div>{{ message }}</div>
    </div>
  </div>
</template>

<script setup lang="ts">
  let message: string = "hello world";
  const changeMsg = () => {
    message = "changed";
  };
</script>

<style lang="scss" scoped></style>
```

Thus, we need to use `Ref`, the TS interface for Ref is:

```ts
interface Ref<T> {
  value: T;
}
```

After we use Ref for message vriable, we need to use `.value` to make an assignment

```html
<template>
  <div>
    <button @click="changeMsg">change</button>
    <div>{{ message }}</div>
  </div>
</template>

<script setup lang="ts">
  import { ref, Ref } from "vue";
  let message: Ref<string> = ref("hello world");

  const changeMsg = () => {
    message.value = "change the world";
  };
</script>

<style></style>
<!-- //--------------------------------ts两种方式 -->
<template>
  <div>
    <button @click="changeMsg">change</button>
    <div>{{ message }}</div>
  </div>
</template>

<script setup lang="ts">
  import { ref } from "vue";
  let message = ref<string | number>("hello world");

  const changeMsg = () => {
    message.value = "change the world";
  };
</script>

<style></style>
```

So, we have two methods to add ts for ref:

1. Import the `Ref` interface from the 'vue'

```ts
import { ref, Ref } from "vue";
let message: Ref<string> = ref("hello world");
```

2. Using the `ref` directly.

```ts
import { ref } from "vue";
let message = ref<string | number>("hello world");
```

## isRef

## shallowRef

## triggerRef

## toRef

## toRefs
