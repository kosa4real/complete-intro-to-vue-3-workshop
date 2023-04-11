<template>
  <div class="grid">
    <div>
      <slot name="one"></slot>
    </div>
    <div>
        <slot name="two"></slot>
      </div>
  </div>
</template>

<script setup>

</script>

<style >
  .grid{
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    border: 3px solid saddlebrown;
  }
</style>