# Reactive Family

It is used to bind complex data types e.g. `objects` or `arrays`.

It can not be used to bind common data type, such as: string, number.

This is a wrong example here:

```js
import {reactive} from 'vue',
let person = reactive('sad')
```

As for how to bind common data, we can use `ref`.

Also, we can use ref to bind objects or arrays complex data types, but when we use reactive to bind them, one benefit is we can directly change the variablevalue without to modify `.value`.

- reactive base useage:

```js
import {reactive} from 'vue',

const person = reactive({
    name:'coco'
}),

person.name = "sky coco"

```

- Array asynchronous assignment problem

  Blow code is not work, because it is out of response.

  ```js
      let person = reactive<number[]>([])
      setTimeout(()=>{
          person = [1,2,3],
          console.log(person)
      },1000)
  ```

  - Solution one:
    Use `push`

    ```js
        import {reactive} from 'vue';
        let person = reactive<number[]>([])
        setTimeout(()=>{
            const arr = [1,2,3]
            person.push(...arr)
            console.log(person)
        },1000)
    ```

    - Solution Two:
      Wrapping a layer of `object` outside.

    ```ts
    import { reactive } from "vue";
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

- readonly

  Make a copy of the proxy object and make it read-only

  ```ts
  import { reactive, readonly } from "vue";
  const figures = reactive({ count: 1 });
  const copy = readonly(figures);

  //figures.count++ the value will be changed
  copy.count++; // this will not be changed
  ```

- shallowReactive

  Only for shallow data If it is `deep data` only the value will be changed not the view

  example:

  ```ts
      <template>
          <div>
              <div>{{state}}</div>
              <button @click="change1">test1</button>
              <button @click="change2">test2</button>
              <button @click="change3">test2</button>
          </div>
      </template>

      <script setup lang="ts">
        import {shallowReactive} from 'vue';

        const foo = {
            a:1,
            first:{
                b:2,
                second:{
                    c:3
                }
            }
        }

        const state = shallowReactive(foo)
        // view will change
        function change1(){
            state.a = 7
        }

        // view will not change
        function change2(){
            state.first.b = 8
            state.first.second.c = 9
            console.log(state);
        }

        // all will change
        function change3(){
            state.a = 7
            state.first.b = 8
            state.first.second.c = 9
            console.log(state);
        }

      </script>
  ```
