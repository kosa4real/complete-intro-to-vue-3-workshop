<script>
export default {
  props: {
    players: {
      type: Array,
      required: true,
    }
  },
  computed: {
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
}
</script>
<template>
  <h2>Players Stats</h2>
  <!-- <p>{{playerStatistics}}</p> -->
  <ul>
    <li v-for="(player, key) in playerStatistics" :key="`player-${key}`">{{ key }}: {{ player }}</li>
  </ul>
  <hr />
</template>