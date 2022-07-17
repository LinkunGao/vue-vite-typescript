# toRef toRefs toRaw

## toRef

- if the origin object is not responsive, the view will not be update. but the date will change.

```html
<template>
  <div>
    <button @click="change">click</button>
    {{state}}
  </div>
</template>
```

```ts
import { reactive, toRef } from "vue";
const obj = {
  foo: 1,
  bar: 1,
};

const state = toRef(obj, "bar");

const change = () => {
  state.value++;
  console.log(obj, state);
};
```

- if the origin object is responsive, it will cause view and change the data.

## toRefs

- can help us to create ref objects in bulk mainly to facilitate our deconstruction use.

```ts
import { reactive, roRefs } from "vue";

const obj = reactive({
  foo: 1,
  bar: 1,
});
let { foo, bar } = toRefs(obj);

foo.value++;
console.log(foo, bar);
```

## toRaw

change responsive object to non-responsive object

```ts
import { reactive, toRaw } from "vue";

const obj = reactive({
  foo: 1,
  bar: 1,
});
const state = toRaw(obj);
const change = () => {
  console.log(obj, state);
};
```
