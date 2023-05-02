<template>
  <div class="name">{{ name }}</div>
  <div class="name">{{ object.name }}</div>
  <button
      v-on:click="updateName "
  >
    Click
  </button>
  <div>
    {{price1}}
  </div>
  <div>
    {{price2}}
  </div>
</template>

<script>

import { ref } from 'vue';
import { reactive } from 'vue';

export default {
  setup() {
    const name = ref('KYS');

    const object = reactive({
      id: 1,
      name: 'hello'
    });

    // setup 함수 안에서 여러개 함수를 만들어서 사용할 수 있다.
    const greeting = (name) => {
      return 'hello ' + name.value;
    };

    const greet = greeting(name);

    const consoleLog = () => {
      console.log('Hello World');
    }

    const updateName = () => {
      name.value = 'YoungSik';
      object.name = 'change';
      console.log(name);
    };

    return {
      name,
      greet,
      consoleLog,
      updateName,
      object,
    };
  },

  data() {
    return {
      price1 : 60,
      price2 : 70,
    }
  }

  // 문법을 왜쓰는지 용도를 알아야 한다.
  // {{ }} 왜 쓸까? , 언제 쓸까?
  // 뷰가 제공하는 실시간 자동 렌더링 사용을 위해
}
</script>

<style>
.name {
  color: red;
}
</style>