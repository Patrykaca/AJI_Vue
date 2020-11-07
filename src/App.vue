<template>
  <div id="app">
    <Search />
    <GenreFilmsList />
    <CastFilmsList />
    <FilmsTable />
    <Background/>
  </div>
</template>

<script>

import Search from './components/Search.vue'
import GenreFilmsList from './components/GenreFilmsList.vue'
import CastFilmsList from './components/CastFilmsList.vue'
import FilmsTable from './components/FilmsTable.vue'
import Background from "@/components/Background";

export default {
  name: 'App',
  components: {
    Background,
    Search,
    GenreFilmsList,
    CastFilmsList,
    FilmsTable,
  }
}
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@300;400;600;800&display=swap');

* {
  box-sizing: border-box;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

body {
  font-family: Monteserrat, sans-serif;
  margin: 0;
  padding: 0;
}

#app { /*
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  */
}
</style>
