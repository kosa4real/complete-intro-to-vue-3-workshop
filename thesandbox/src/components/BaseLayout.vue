<template>
  <div class="wrapper">
    <aside class="sidebar">
      <slot name="sidebar"></slot>
    </aside>
    <main>
      <slot name="main"></slot>
    </main>
  </div>
  <footer>
    <slot name="footer"></slot>
  </footer> 
</template>

<script setup>

</script>

<style ></style>