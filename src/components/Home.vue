<template>
  <div>
    <h1 class="navbar">Monster Slayer</h1>

    <div>
      <h1>
        <h1 class="heading">Monster Health</h1>
        <p class="sub-heading">{{ monosterHealth }}</p>
      </h1>
    </div>
    <div>
      <h1>
        <h1 class="heading">Your Health</h1>
        <div v-if="playerHealth > 0">
          <p class="sub-heading">{{ playerHealth }}</p>

          <button class="btn" @click="attackMonoster">Attact</button>

          <button
            class="btn"
            @click="specialAttack"
            :disabled="mayUseSpecialAttack"
          >
            Special attack
          </button>
          <button class="btn" @click="heal">heal</button>
          <button class="btn">surrender</button>
        </div>
        <p class="sub-heading" v-else>
          Game Over Monostor Win the Game !! Better Luck Next Time
        </p>
      </h1>
    </div>

    <!--  -->
  </div>
</template>
<script>
export default {
  name: 'Home',
  data() {
    return {
      monosterHealth: 100,
      playerHealth: 100,
      current: 0,
    };
  },
  methods: {
    attackMonoster() {
      const attackDamage = Math.floor(Math.random() * 5 - 3) + 3;
      this.monosterHealth -= attackDamage;
      this.attackPlayer();
    },
    attackPlayer() {
      const attackDamage = Math.floor(Math.random() * (10 - 5)) + 5;
      this.playerHealth -= attackDamage;
    },
    specialAttack() {
      this.current++;
      const attackDamage = Math.floor(Math.random() * (10 - 8) + 8);
      this.monosterHealth -= attackDamage;
      this.attackPlayer();
      // alert('you cannit use two times at on');
    },
    heal() {
      this.current++;
      const attackDamage = Math.floor(Math.random() * (20 - 8) + 8);
      if (this.playerHealth + attackDamage > 100) {
        this.playerHealth = 100;
      } else {
        this.playerHealth += attackDamage;
      }
      this.attackPlayer();
    },
  },
  computed: {
    mayUseSpecialAttack() {
      return this.current % 3 !== 0;
    },
  },
};
</script>

<style scoped>
.navbar {
  background-color: rgba(255, 0, 0, 0.761);
  color: #ffffffff;
  font-size: 30px;
  font-weight: bold;
}
.heading {
  font-size: 25px;
  font-weight: bold;
  text-align: center;
  color: #000000;
}
.btn {
  padding: 20px;
  border-radius: 20px;
  color: #ffffffff;
  background-color: rgb(43, 12, 43);
  display: block;
  margin: 15px auto;
  width: 20%;
  text-transform: uppercase;
}
.sub-heading {
  background: rgb(124, 186, 124);
  color: #ffffffff;
  font-size: 24px;
  /* margin: 35px 0; */
  /* height: 75px; */
  padding: 16px;
}
</style>
