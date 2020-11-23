<template>
  <div class="searchWrapper">
    <h1>Movies database</h1>
    <input
        id="search"
        name="search"
        type="text"
        placeholder="Title"
    />
    <button v-on:click="searchDB()" class="btn">
      Search
    </button>

    <MoviesTable :jsonDatabase="jsonFiltered"/>
  </div>


</template>

<script>
import lodash from "lodash";
import MoviesTable from "@/components/MoviesTable";

export default {
  name: "Search",
  components: {
    MoviesTable
  },
  props: {
    jsonDatabase: Array,
  },

  data() {
    return {
      jsonFiltered: lodash.cloneDeep(this.jsonDatabase),
      searchVal: {
        title: "",
      },
    }
  },

  methods: {

    isFilled: function (val) {
      return val !== "";
    },

    isInputFilled: function () {
      if (!this.isFilled(this.searchVal.title)) {
        return true;
      }
      return false;
    },

    searchDB: function () {
      // for (let movie in this.jsonDatabase) {

    }
  },
}
</script>

<style lang="scss" scoped>

.searchWrapper {
  display: flex;
  flex-direction: column;
  align-content: center;
  align-items: center;
  justify-content: center;
  font-size: 34px;
  margin-bottom: 10px;
}


</style>
