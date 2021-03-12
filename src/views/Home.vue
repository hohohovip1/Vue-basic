<template>
  <div class="home">
    <h1>Home</h1>
    <p>My name is {{ name }} and my age is {{ age }}</p>
    <button @click="handleClick">click me</button>
    <button @click="age++">Add 1</button>
    <input type="text" v-model="name" />
  </div>
</template>

<script>
import { ref, reactive } from 'vue';

export default {
  name: 'Home',
  setup() {
    const name = ref('mario');
    const age = ref(30);

    const handleClick = () => {
      name.value = 'luigi';
      age.value = 35;
    };
    return {
      name,
      age,
      handleClick,
    };
  },
};
</script>
