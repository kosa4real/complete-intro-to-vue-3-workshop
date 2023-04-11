<template>
  <div>
    <p>{{ player.name }}</p>
    <button @click="addFavoritePlayer">::star</button>
  </div>
</template>

<script >
export default {
  props: {
    player: {
      type: Object,
      required: true
    }
  },
  emits: ['favorite'],
  methods: {
    addFavoritePlayer() {
      this.$emit('favorite', this.player)
    },
  }
}

</script>

<style scoped></style>