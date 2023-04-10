<script >
import PlayerStats from "./components/PlayerStats.vue";
export default {
  components: {
    PlayerStats
  },
  data: () => ({
    newPlayer: {
      name: "",
      position: "",
      age: "",
    },
    players: [
      { name: "Lewandowski", position: "attack", age: 27 },
      { name: "Gavi", position: "midfield", age: 24 },
      { name: "Pedri", position: "midfield", age: 22 },
      { name: "Dembele", position: "wing", age: 28 },
      // { name: "Puyol", position: "wing", age: 36 },
    ],
    favoriteList: [],
  }),

  methods: {
    favoritePlayer(player) {
      this.favoriteList.push(player);
    },
    addNewPlayer() {
      this.players.push(this.newPlayer);
      this.newPlayer = {
        name: "",
      };
    },
  },
}
</script>

<template>
  <PlayerStats :players="players"/>

  <p v-if="players.length === 0">There are no players</p>
  <ul v-else-if="players.length % 2 === 0">
    <li v-for="(player, index) in players" :key="`player-${index}`">
      <p>{{ player.name }}</p>
      <button @click="favoritePlayer(player)">::star</button>
    </li>
  </ul>
  <p v-else>There are odd players</p>
  <h2>Favorite Players</h2>
  <ul v-if="favoriteList.length > 0">
    <li v-for="(fav, index) in favoriteList" :key="`fav-${index}`">{{ fav.name }}</li>
  </ul>
  <p v-else>No favorite player yet</p>
  <hr />
  <h2>New Player</h2>
  <pre>
                {{ newPlayer }}
              </pre>
  <label for="character-name">Name</label>
  <input type="text" v-model="newPlayer.name" @keyup.enter="addNewPlayer" />
  <p>
    <span v-for="(player, index) in players" :key="`player-${index}`">{{ player.name }}{{ index === players.length - 1 ?
      '' : ', ' }}</span>
  </p>
</template>

<style scoped></style>
