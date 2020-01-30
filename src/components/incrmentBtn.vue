<template>
  <div class="incrementBtn__container">
    <p class="incrementBtn__container__number">{{value}}</p>
    <button v-on:click="updateValue('-')" class="btn incrementBtn__container__btn btn_neg">
      -
    </button>
    <button v-on:click="updateValue('+')" class="btn incrementBtn__container__btn btn_pos">
      +
    </button>
  </div>
</template>

<script>
export default {
  name: 'incrmentBtn',
  props: {
    value: {
      type: Number,
      required: true,
    },
  },
  // data() {
  //   return {
  //     value: 0,
  //   };
  // },
  methods: {
    updateValue(operator) {
      switch (operator) {
        case '-':
          this.$emit('newValue', this.value - 1);
          break;

        case '+':
          this.$emit('newValue', this.value + 1);
          break;

        default:
          /* eslint-disable no-console */
          console.error('There is an error while mapping the action');
          break;
      }
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
p {
  margin: 0;
}

.incrementBtn__container {
  display: flex;
  align-items: center;

  width: 150px;

  margin: 10px auto;
  padding: 5px 10px;

  background-color: black;

  border-radius: 5px;
}

.incrementBtn__container__number {
  margin: auto;
  color: white;
  font-weight: bold;
  font-size: 1.5em;
}

.incrementBtn__container__btn {

  height:30px;
  width:30px;

  margin: 5px;
  padding: 5px;

  line-height:0;
}

.btn_neg {
  background-color: #2a2f33;
  border-color: #464d54;
}

.btn_neg:focus {
  box-shadow: 0 0 0 0.2rem rgba(52,58,64,.5);
}

.btn_pos {
  background-color: #28a745;
  border-color: #28a745;
}

.btn_pos:focus {
}
</style>
