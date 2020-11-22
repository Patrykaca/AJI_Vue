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
        <tr class="tableJson" v-for="(index, val) in tableSize" :key="val">
            <th>{{jsonDatabase[val].title}}</th>
            <th>{{jsonDatabase[val].year}}</th>
            <th>{{jsonDatabase[val].cast.toString().split(",").join(", ")}}</th>
            <th>{{jsonDatabase[val].genres.toString().split(",").join(", ")}}</th>
        </tr>
      </tbody>
    </table>

    <div>
      <button class="btn btn-block" v-on:click="expand">Next</button>
    </div>

  </div>
</template>

<script>
const TABLE_SIZE = 100;
let tableSize;

export default {

  name: "MoviesTable",

  props: {
    jsonDatabase: Array,
  },

  data() {
    tableSize = TABLE_SIZE;

    if (this.jsonDatabase.length < TABLE_SIZE) {
      tableSize = this.jsonDatabase.length;
    } else {
      tableSize = TABLE_SIZE;
    }

    return {
      tableSize,
    }
  },

  methods: {
    expand() {
      if (this.jsonDatabase.length + TABLE_SIZE <= this.tableSize) {
        this.tableSize = this.jsonDatabase.length;
      } else {
        this.tableSize += TABLE_SIZE;
      }
    }
  },
}
</script>

<style lang="scss" scoped>

.tableWrapper {
  margin-left: 10px;
  margin-right: 10px;
  padding: 10px;
  display: flex;
  flex-direction: column;
  align-content: center;
  align-items: center;
  justify-content: center;
}

.mainTh {
  margin-left: 10px;
  margin-right: 10px;
  font-size: 40px;
  padding: 0 20px 0 20px;
  letter-spacing: 2px;
  font-weight: 400;
  color: #4a4a4a;
  text-shadow: 0 0 5px rgba(94, 171, 94, 0.4);
}

.tableJson {
  font-size: 11px;
}

</style>
