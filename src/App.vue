<template>

  <div id="app">
    <Search />
    <FilmsTable />
    <GenreFilmsList />
    <CastFilmsList />
  </div>
</template>

<script>

import Search from './components/Search.vue'
import GenreFilmsList from './components/GenreFilmsList.vue'
import CastFilmsList from './components/CastFilmsList.vue'
import FilmsTable from './components/FilmsTable.vue'

import json from '../data/movies.json'

      export default{
        name: 'App',
        components: {
          Search,
          GenreFilmsList,
          CastFilmsList,
          FilmsTable
        },
          data(){
              return{
                  myJson: json
                 
      
              }
          }
      }
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
