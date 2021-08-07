<template>
  <div>
    <h1>{{ data }}</h1>
    <button @click="add()">Increment</button>
    <button @click="decrement()">Decrese</button>
    <h3>{{ this.counter }}</h3>

    <form @submit.prevent="formSubmit">
      <input type="text" v-model="name" />
      <button>Submit</button>
    </form>
  </div>
</template>
<script>
export default {
  name: 'Home',
  data() {
    return {
      counter: 0,
      name: '',
    };
  },
  props: {
    data: String,
  },
  watch: {
    counter(value) {
      if (value > 5) {
        this.counter = 0;
      }
    },
  },
  methods: {
    formSubmit() {
      alert('form submitted');
      //
    },

    add() {
      this.counter = this.counter + 1;
    },
    decrement() {
      this.counter = this.counter - 1;
    },
  },
};
</script>
