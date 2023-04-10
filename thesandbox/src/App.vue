<script>
export default {
  data() {
    return {
      count: 0,
      incrementAmount: 1,
      counterTitle: "Standard Counter",
      message: "Hello it works",
      listOfNumbers: [
        {
          name: 1,
          id: "4617b4fa-a4f7-4b14-a094-a80b51d604fb",
          list: [1, 2, 3],
        },
        {
          name: 2,
          id: "97df1a19-5246-430b-a8fe-a2d54bbfbf75",
          list: [1, 2, 3],
        },
        {
          name: 3,
          id: "7e6608ad-072f-4c79-a092-489b3a27128b",
          list: [1, 2, 3],
        },
        {
          name: 4,
          id: "1d53f71c-140e-4c2c-80ec-305b5bb8944d",
          list: [1, 2, 3],
        },
        {
          name: 5,
          id: "a9a3eb4f-1dc7-4b4e-86ca-e628c8375588",
          list: [1, 2, 3],
        },
      ],
    };
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
  watch: {
    count(newValue, oldValue) {
      // console.log("NEW",newValue)
      // console.log("OLD",oldValue)
      if (newValue >= 20) {
        this.counterTitle += " Very Long";
        // unwatch()
      }
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
  <hr />
  <p v-if="message.length % 2 === 0">Even: {{ message.toUpperCase() }}</p>
  <p v-else>Odd: {{ message }}</p>
  <ul>
    <li v-for="(item, index) in listOfNumbers" :key="`item-${index}`">
      {{ item.id }}
      <ul>
        <li v-for="(number, index) in item.list" :key="`number-${index}`">{{ number }}</li>
      </ul>
    </li>
  </ul>
  <hr />
</template>

<style scoped></style>
