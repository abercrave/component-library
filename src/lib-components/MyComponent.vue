<template>
  <div class="my-component">
    <p>
      The counter was {{ changedBy }} to <b>{{ counter }}</b
      >.
    </p>
    <MyButton @click="increment">
      Click +1
    </MyButton>
    <MyButton @click="decrement">
      Click -1
    </MyButton>
    <MyButton @click="increment(5)">
      Click +5
    </MyButton>
    <MyButton @click="decrement(5)">
      Click -5
    </MyButton>
    <MyButton @click="reset">
      Reset
    </MyButton>
  </div>
</template>

<script>
import MyButton from "./MyButton.vue";
export default {
  name: "MyComponent", // vue component name
  components: { MyButton },
  data() {
    return {
      counter: 5,
      initCounter: 5,
      message: {
        action: null,
        amount: null,
      },
    };
  },
  computed: {
    changedBy() {
      const { message } = this;
      if (!message.action) return "initialized";
      return `${message?.action} ${message.amount ?? ""}`.trim();
    },
  },
  methods: {
    increment(arg) {
      const amount = typeof arg !== "number" ? 1 : arg;
      this.counter += amount;
      this.message.action = "incremented by";
      this.message.amount = amount;
    },
    decrement(arg) {
      const amount = typeof arg !== "number" ? 1 : arg;
      this.counter -= amount;
      this.message.action = "decremented by";
      this.message.amount = amount;
    },
    reset() {
      this.counter = this.initCounter;
      this.message.action = "reset";
      this.message.amount = null;
    },
  },
};
</script>

<style scoped>
.my-component {
  display: block;
  width: 400px;
  margin: 25px auto;
  border: 1px solid #ccc;
  background: #eaeaea;
  text-align: center;
  padding: 25px;
}
.my-component p {
  margin: 0 0 1em;
}
</style>
