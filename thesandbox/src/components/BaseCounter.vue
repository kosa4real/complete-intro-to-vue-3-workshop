<script>
export default {
  data() {
    return {
      count: 0,
      incrementAmount: 1,
      counterTitle: "Standard Counter",
    }
  },
  computed: {
    displayTitle() {
      if (this.count > 20) {
        return "Counter Standard - Very Long";
      } else {
        return "Counter Standard";
      }
    },

    optimizedIncrementAmount() {
      return this.displayTitle.length * this.incrementAmount;
    },
  },
  methods: {
    incrementCount(newAmt, event) {
      console.log(newAmt);
      console.log(event);
      this.count += this.optimizedIncrementAmount;
    },
  },
}
</script>
<template>
  <h1>{{ displayTitle }}</h1>
  <p :data-increment-by="incrementAmount">{{ count }}</p>
  <button @click="incrementCount(10, $event)">Increment Count</button>
  <h1>{{ incrementAmount }}</h1>
  <h2>{{ optimizedIncrementAmount }}</h2>
  <div>
    <label for="incrementAmount">Increment by: </label>
    <input type="number" v-model="incrementAmount" />
  </div>
</template>