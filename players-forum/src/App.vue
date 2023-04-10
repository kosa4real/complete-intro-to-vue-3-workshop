<script >
export default {
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

  computed: {
    // strikers() {
    //   return this.players.filter(
    //     (player) => player.position.indexOf("attack") > -1
    //   );
    // },
    playerStatistics() {
      const positions = ["midfield", "wing", "attack", "defense"];
      const statistics = {
        midfield: 0,
        attack: 0,
        wing: 0,
        defense: 0,
      };

      this.players.forEach((player) => {
        positions.forEach((position) => {
          if (player.position.indexOf(position) > -1) {
            statistics[position] += 1;
          }
        });
      });

      return statistics;
      // alternative using reduce
      //const result = players.reduce((groupedPlayer, player)=>{
      // const position = player.position;
      // if(groupedPlayer[position] == null) {
      //   groupedPlayer[position] = []
      // }
    },
  },

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
  <h2>Players Stats</h2>
  <!-- <p>{{playerStatistics}}</p> -->
  <ul>
    <li v-for="(player, key) in playerStatistics" :key="`player-${key}`">{{ key }}: {{ player }}</li>
  </ul>
  <hr />
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
    <span v-for="(player, index) in players" :key="`player-${index}`">{{ player.name }}{{ index === players.length - 1 ? '' : ', ' }}</span>
  </p>
</template>

<style scoped></style>
