
<script>
export default {
  props: {
    left: {
      type: Boolean,
      default: false,
    }
  }

}

</script>

<template>
  <button>
    <slot v-if="left">Icon left - Cancel</slot>
    <v-slot v-else>Submit</v-slot>
  </button>
</template>

<style lang="scss" scoped></style>