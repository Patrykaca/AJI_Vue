<template>
  <div class="bgWrapper"/>
</template>

<script>
export default {
name: "Background"
}
</script>

<style lang="scss" scoped>
  .bgWrapper {
    position: fixed;
    top: 0;
    z-index: -1;
    width: 100%;
    height: 100vh;
    background-image: url("https://images.pexels.com/photos/305821/pexels-photo-305821.jpeg?auto=compress&cs=tinysrgb&dpr=3&h=750&w=1260");
    background-repeat: no-repeat;
    background-size: cover;
    background-position: 24% 0;
  }
</style>
