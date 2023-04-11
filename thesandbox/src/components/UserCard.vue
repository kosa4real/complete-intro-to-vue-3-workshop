<script>
export default {
  name: "UserCard",
  props: {
    userData: {
      type: Object,
      required: true,
    }
  },
  emits: ['change-name'],
  methods: {
    // alternative to emit directly on thebutton
    // tellParentChangeName(){
    //   this.$emit('change-name')
    // }
  }
}
</script>
<template>
  <div>
    <h1>User: {{userData.name}}</h1>
    <p>Framework: {{userData.framework}}</p>
    <button @click="$emit('change-name')">change Name</button>
    <!-- <button @click="tellParentChangeName">change Name</button> -->

  </div>
</template>