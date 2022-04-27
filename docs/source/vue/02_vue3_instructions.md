# Vue3 指令

v- 开头都是 vue 的指令

v-text 用来显示文本

v-html 用来展示富文本

```html
<template>
  <div v-html="message"></div>
</template>
<script setup lang="ts">
  const message: string = "<div>Hello world</div>";
</script>
```

v-if 用来控制元素的显示隐藏（切换真假 DOM）

v-else-if 表示 v-if 的“else if 块”。可以链式调用

v-else v-if 条件收尾语句

v-show 用来控制元素的显示隐藏（display none block Css 切换）

```html
<template>
  <div v-show="flag === 'C' ? true : false">show</div>
</template>
<script setup lang="ts">
  const flag: string = "C";
</script>
```

v-on 简写@ 用来给元素添加事件

```html
<template>
  <div v-on:click="clickMeOne">Click me One</div>
  <div @click="clickMeTwo">Click me Two</div>
</template>
<script setup lang="ts">
  const clickMeOne = () => {
    console.log("Click me One");
  };
  const clickMeTwo = () => {
    console.log("It's me");
  };
</script>
```

v-bind 简写: 用来绑定元素的属性 Attr

```html
<template>
  <div :class="flag ? 'a' : 'b'">hello world</div>
</template>

<script setup lang="ts">
  const flag: boolean = false;
</script>

<style scoped>
  .a {
    color: red;
  }
  .b {
    border: 1px solid salmon;
  }
</style>
```

v-model 双向绑定 一般用于绑定表单元素 需要配合 `ref()` 等函数来使用,将 v-model 下的变量变为响应式变量

```html
<template>
  <input v-model="tag" type="text" />
  {{ tag }}
</template>
<script setup lang="ts">
  import { ref } from "vue";
  const tag = ref("test");
</script>
```

v-for 用来遍历元素

v-on 修饰符 冒泡案例 .stop .prevent

```html
<template>
  <div v-on:click="parent">
    <div v-on:click.stop="clickMeOne">Click me One</div>
  </div>
</template>
<script setup lang="ts">
  const parent = () => {
    console.log("parent");
  };
  const clickMeOne = () => {
    console.log("Click me One");
  };
</script>
```
