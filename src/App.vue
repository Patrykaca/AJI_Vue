<template>
  <div id="app">
    <Search />
    <GenreFilmsList />
    <CastFilmsList />
    <MoviesTable/>
    <Background/>
  </div>
</template>

<script>

import Search from './components/Search.vue'
import GenreFilmsList from './components/GenreFilmsList.vue'
import CastFilmsList from './components/CastFilmsList.vue'


import json from './assets/movies.json'
import MoviesTable from "@/components/MoviesTable";
import Background from "@/components/Background";

      export default{
        name: 'App',
        components: {
          Background,
          MoviesTable,
          Search,
          GenreFilmsList,
          CastFilmsList,
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
