<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld/>
    <div style="height: 25px;">
      <p v-if="average === 3" style="margin: 0; font-weight: bold;">
        Average is 3, congratulation 🎉
      </p>
    </div>
    <incrmentBtn @newValue="counter1 = $event" :value="counter1"/>
    <incrmentBtn @newValue="counter2 = $event" :value="counter2"/>
    <incrmentBtn @newValue="counter3 = $event" :value="counter3"/>
    <p>Moyenne : {{ average }}</p>
    <button v-on:click="resetCounter" class="btn btn__reset">RESET</button>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue';
import incrmentBtn from './components/incrmentBtn.vue';

export default {
  name: 'app',
  components: {
    HelloWorld,
    incrmentBtn,
  },
  data() {
    return {
      counter1: 0,
      counter2: 0,
      counter3: 0,
    };
  },
  methods: {
    resetCounter() {
      this.counter1 = 0;
      this.counter2 = 0;
      this.counter3 = 0;
    },
  },
  computed: {
    average() {
      return Math.round(((this.counter1 + this.counter2 + this.counter3) / 3) * 100) / 100;
    },
  },
};
</script>

<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.btn {
  margin: 5px;
  padding: 5px;

  background-color:rgb(84, 91, 98);

  border: 1px solid rgb(78, 85, 91);
  border-radius: 5px;

  font-family: Roboto;
  font-weight: bold;
  font-size: 1.5em;
  text-align:center;
  color:rgb(255, 255, 255);
}

.btn__reset {
  padding: 2px 7px;

  background-color: #c82333;
  border-color: #bd2130;

  font-weight: normal;
}
</style>
