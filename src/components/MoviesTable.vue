<template>
  <div class="tableWrapper">
    <table class="table">
      <thead>
      <tr>
        <th class="mainTh">Title</th>
        <th class="mainTh">Year</th>
        <th class="mainTh">Cast</th>
        <th class="mainTh">Genres</th>
      </tr>
      </thead>
      <tbody>
        <tr class="tableJson" v-for="(index, val) in jsonDatabase" :key="val">
            <th>{{jsonDatabase[val].title}}</th>
            <th>{{jsonDatabase[val].year}}</th>
            <th>{{jsonDatabase[val].cast.toString()}}</th>
            <th>{{jsonDatabase[val].genres.toString()}}</th>
        </tr>
      </tbody>
    </table>
    <div> {{ jsonDatabase[0] }}
    </div>
  </div>
</template>

<script>

export default {
  name: "MoviesTable",
  props: {
    jsonDatabase: Array,
  },
}
</script>

<style lang="scss" scoped>

.tableWrapper {
  display: flex;
  flex-direction: column;
  align-content: center;
  align-items: center;
  justify-content: center;
}

.mainTh {
  font-size: 40px;
  padding: 0 20px 0 20px;
  letter-spacing: 2px;
  font-weight: 400;
  color: #4a4a4a;
  text-shadow: 0 0 5px rgba(94, 171, 94, 0.4);
}

.tableJson {
  font-size: 7px;
}

</style>
