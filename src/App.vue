<template>
  <div id="app">
    <Search />
    <MoviesGenre/>
    <MoviesCast/>
    <MoviesTable/>
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

      export default{
        name: 'App',
        components: {
          MoviesGenre,
          MoviesCast,
          Background,
          MoviesTable,
          Search,
        },
          data(){
              return{
                  myJson: json


              }
          }
      }
</script>

<style lang="scss" scoped>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
