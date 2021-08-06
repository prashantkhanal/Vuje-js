<template>
  <div>
    <h1>{{ data }}</h1>
    <button v-on:click="add()">Increment</button>
    <button v-on:click="decrement()">Decrese</button>
    <h3>{{ this.counter }}</h3>
  </div>
</template>
<script>
export default {
  name: 'Home',
  data() {
    return {
      counter: 0,
    };
  },
  props: {
    data: String,
  },
  methods: {
    add() {
      this.counter = this.counter + 1;
    },
    decrement() {
      this.counter = this.counter - 1;
    },
  },
};
</script>
