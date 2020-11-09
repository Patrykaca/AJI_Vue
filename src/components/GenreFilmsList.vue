<template>
    <div>
      <p>gene </p>
      <div  v-for="data in myJson" v-bind:key="data" >{{data.title}}</div>
    </div>
</template>

<script>
export default {
  name: "GenreFilmsList"
}
</script>

<style scoped>

</style>
