<template>
  <div class="hello">
    <h1>{{ inputCount }}</h1>
    <button @click="decrement">-</button>
    <input type="number" v-model="inputCount" @input="updateCount" />
    <button @click="increment">+</button>
  </div>
</template>

<script>
import { mapActions, mapGetters } from "vuex";
export default {
  name: "HelloWorld",
  computed: {
    ...mapGetters(["getCount"]),
    inputCount: {
      get() {
        return this.getCount;
      },
      set(value) {
        this.setCount(Number(value)); // update store count based on input
      },
    },
  },
  methods: {
    ...mapActions(["increment", "decrement", "setCount"]),
    updateCount(event) {
      this.setCount(Number(event.target.value)); // update store count based on input change
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped></style>
