<script >
import BaseLayout from "./components/BaseLayout.vue";
import PlayerStats from "./components/PlayerStats.vue";
import PlayerCard from "./components/PlayerCard.vue";
export default {
  components: {
    BaseLayout,
    PlayerStats,
    PlayerCard
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

    addNewPlayer() {
      this.players.push(this.newPlayer);
      this.newPlayer = {
        name: "",
      };
    },
    addFavoritePlayer(payload) {
      this.favoriteList.push(payload)
    }
  },
}
</script>

<template>
  <BaseLayout>
    <template v-slot:one>
      <h2>New Player</h2>
      <pre>
        {{ newPlayer }}
      </pre>
      <label for="character-name">Name</label>
      <input type="text" v-model="newPlayer.name" @keyup.enter="addNewPlayer" />
      <p>
        <span v-for="(player, index) in players" :key="`player-${index}`">{{ player.name }}{{ index === players.length - 1
          ?
          '' : ', ' }}</span>
      </p>
    </template>
  </BaseLayout>
  <PlayerStats :players="players" />

  <p v-if="players.length === 0">There are no players</p>
  <ul v-else-if="players.length % 2 === 0">
    <li v-for="(player, index) in players" :key="`player-${index}`">
      <PlayerCard :player="player" @favorite="addFavoritePlayer" />
    </li>
  </ul>
  <p v-else>There are odd players</p>
  <h2>Favorite Players</h2>
  <ul v-if="favoriteList.length > 0">
    <li v-for="(fav, index) in favoriteList" :key="`fav-${index}`">{{ fav.name }}</li>
  </ul>
  <p v-else>No favorite player yet</p>
  <hr />
</template>

<style scoped></style>
