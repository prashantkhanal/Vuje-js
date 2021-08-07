/* eslint-disable vue/require-v-for-key */
<template>
  <div>
    <h1>Vue Goals</h1>
    <div>
      <h5>my course goals</h5>
      <input type="text" v-model="enteredGoals" />
      <button @click="addGoals">Add Goal</button>
      <p v-if="goals.length === 0">
        Ni goals have been added yet please start adding some!
      </p>
      <ul v-else>
        <li
          v-for="(goal, index) in goals"
          :key="goal"
          @click="removedGoals(index)"
        >
          {{ goal }} - {{ index }}
        </li>
      </ul>
      <h6>This is for the object</h6>
      <ul>
        <li v-for="(value, key, index) in discriptions" :key="index">
          value: {{ value }} <br />
          key: {{ key }}
          <br />
          index:{{ index }}
        </li>
      </ul>
    </div>
  </div>
</template>
<script>
export default {
  name: 'Home',
  data() {
    return {
      goals: [],
      enteredGoals: '',
      discriptions: {
        firstName: 'prashant',
        lastName: 'khanal',
      },
    };
  },
  methods: {
    addGoals() {
      this.goals.push(this.enteredGoals);
    },
    removedGoals(idx) {
      this.goals.splice(idx, 1);
    },
  },
};
</script>
