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
      <tbody class="bodyClass">
        <tr class="tableJson" v-for="(index, val) in tableSize" :key="val">
            <th>{{jsonDatabase[val].title}}</th>
            <th>{{jsonDatabase[val].year}}</th>
            <th>{{jsonDatabase[val].cast.toString().split(",").join(", ")}}</th>
            <th>{{jsonDatabase[val].genres.toString().split(",").join(", ")}}</th>
        </tr>
      </tbody>
    </table>

    <div>
      <button class="btn btn-block" v-on:click="expand()">Show more</button>
    </div>

  </div>
</template>

<script>
const TABLE_SIZE = 10;
let tableSize;

export default {

  name: "MoviesTable",

  props: {
    jsonDatabase: Array,
  },

  data() {
    tableSize = TABLE_SIZE;
    console.log(this.jsonDatabase.length);

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
  margin-left: 120px;
  margin-right: 120px;
  padding: 10px;
  display: flex;
  flex-direction: column;
  align-content: center;
  align-items: center;
  justify-content: center;
  text-align: left;
  background-color: white;
  opacity: 0.8;

}

.mainTh {
  margin-left: 10px;
  margin-right: 10px;
  font-size: 50px;
  padding: 0 20px 0 20px;
  letter-spacing: 2px;
  font-weight: 400;
  color: black;
  text-shadow: 0 0 5px rgba(94, 171, 94, 0.4);
}

.tableJson {
  font-size: 22px;
  /*
  align-content: left;
  align-items: left;
   */
}

.btn{
  font-size: 30px;
  margin-top: 20px;
}
</style>
