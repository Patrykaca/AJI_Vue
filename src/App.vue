<template>
  <div id="app">
    <!-- <div>{{moviesData[0]}}</div>
    -->
    <Search />
    <p></p>
    <MoviesGenre/>
    <MoviesCast/>
    <MoviesTable :jsonDatabase="moviesData"/>
    <Background/>
  </div>
</template>

<script>
import json from './assets/movies.json'
import Search from './components/Search.vue'
import MoviesTable from "@/components/MoviesTable";
import Background from "@/components/Background";
import MoviesCast from "@/components/MoviesCast";
import MoviesGenre from "@/components/MoviesGenre";

export default {
  name: 'App',
  components: {
    MoviesGenre,
    MoviesCast,
    Background,
    MoviesTable,
    Search,
  },
  data() {
    return {
      moviesData: json,
    };
  },
  methods: {
    sendJson() {
      return this.moviesData;
    },
  },
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

body {
  margin: 0;
  padding: 0;
}
</style>
