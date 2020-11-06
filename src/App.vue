<template>
  <div id="app">
    <Search />
    <GenreFilmsList />
    <CastFilmsList />
    <FilmsTable />
  </div>
</template>

<script>

import Search from './components/Search.vue'
import GenreFilmsList from './components/GenreFilmsList.vue'
import CastFilmsList from './components/CastFilmsList.vue'
import FilmsTable from './components/FilmsTable.vue'

export default {
  name: 'App',
  components: {
    Search,
    GenreFilmsList,
    CastFilmsList,
    FilmsTable
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
