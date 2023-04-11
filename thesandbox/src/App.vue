<script>
import BaseButton from "./components/BaseButton.vue";
import BaseCounter from "./components/BaseCounter.vue";
import BaseLayout from "./components/BaseLayout.vue";
import UserCard from "./components/UserCard.vue";
export default {
  components: {
    BaseButton,
    BaseCounter,
    BaseLayout,
    UserCard,
  },
  data() {
    return {
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
      userData: {
        name: "Munir",
        prefferedFramework: "vue",
        favoriteDish: "any",
        favoriteNumbers: [3, 4, 5]
      }
    };
  },

  computed: {
    refinedData() {
      return {
        name: this.userData.name,
        framework: this.userData.prefferedFramework
      }
    }
  },
  methods: {
    changeName() {
      this.userData.name = "Abdul"
    }
  }


}
</script>

<template>
  <BaseLayout>
    <template v-slot:sidebar>
      <h1>Slot Header</h1>
      <hr>
    </template>
    <template v-slot:main>
      <div style="display: flex; justify-content:space-around">
        <div>One</div>
        <div>Two</div>
        <div>Three</div>
      </div>
    </template>
    <template v-slot:footer>
      <p style="text-align:center">&copy;2023</p>
    </template>

  </BaseLayout>
  <BaseButton left="true"></BaseButton>
  <UserCard :userData="refinedData" @change-name="changeName" />
  <BaseCounter />
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
