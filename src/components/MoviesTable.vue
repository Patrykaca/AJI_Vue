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
      <tbody class="bodyClass"> <!-- v-for="val" nie wyswietla 1 filmu -->
        <tr class="tableJson" v-for="(index, val) in tableSize" :key="val">
            <th>{{jsonDatabase[val].title}}</th>
            <th>{{jsonDatabase[val].year}}</th>
            <th>{{jsonDatabase[val].cast.toString().split(",").join(", ")}}</th>
            <th>{{jsonDatabase[val].genres.toString().split(",").join(", ")}}</th>
        </tr>
      </tbody>
    </table>

    <div>
      <button class="btnClass" v-on:click="expand()">Show more</button>
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

.btnClass {
  width: 360px;
  height: 40px;
  align-content: center;
  margin-top: 15px;
  margin-bottom: 15px;
  border-radius: 15px;
  border-style: groove;
  font-size: 20px;
  font-weight: 500;
  letter-spacing: 2px;
  transition: box-shadow 0.1s ease-in-out;
}

.btnClass:hover {
  -webkit-box-shadow: inset 0px 0px 8px 5px rgba(0, 0, 0, 0.1);
  -moz-box-shadow: inset 0px 0px 8px 5px rgba(0, 0, 0, 0.1);
  box-shadow: inset 0px 0px 8px 5px rgba(0, 0, 0, 0.1);
}
</style>
