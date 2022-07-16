# Reactive

- It used to bind complex data type, such as `Object Array`.
- It cannot be used to bind common data type, such as `number boolean string`.

If we use `Ref` to bind data, it also call reactive.

When we use reactive, we don't need to use .value if we want to change the value.

```ts
import { reactive } from "vue";
let person = reactive({
  name: "coco",
});

person.name = "skycoco";
```

## Array asynchronous assignment problem

when we assign value like this, the page value will not be changed, that's because it out of responsive.

```ts
let person = reactive<number[]>([]);
setTimeout(() => {
  person = [1, 2, 3];
  console.log(person);
}, 1000);
```

### soluion 1

- use Array.push

```ts
import { reactive } from "vue";
let person = reactive<number[]>([]);
setTimeout(() => {
  const arr = [1, 2, 3];
  person.push(...arr);
  console.log(person);
}, 1000);
```

### solution 2

- use an object outside

```ts
type Person = {
  list?: Array<number>;
};
let person = reactive<Person>({
  list: [],
});
setTimeout(() => {
  const arr = [1, 2, 3];
  person.list = arr;
  console.log(person);
}, 1000);
```

## readonly

- copy a `proxy` object and set it to readonly

```ts
import { ractive, readonly } from "vue";
const person = reactive({ count: 1 });
const copy = readonly(person);

copy.count++;
```

## shallowReactive

- only focus on shallow data, if change the deep data, it can not change the view.

```html
<template>
  <div>
    <div>{{state}}</div>
    <button @click="change1">test1</button>
    <button @click="change2">test2</button>
  </div>
</template>
```

```ts
import { shallowReactive } from "vue";

const obj = {
  a: 1,
  first: {
    b: 2,
    second: {
      c: 3,
    },
  },
};

const state = shallowReactive(obj);
function change1() {
  state.a = 7;
}
function change2() {
  state.first.b = 8;

  state.first.second.c = 7;

  console.log(state);
}
```
