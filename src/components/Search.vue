<template>
  <div class="searchWrapper">
    <h1>Movies database</h1>
    <input
        id="search"
        name="search"
        type="text"
        placeholder="Title"
        v-model="searchVal.title"
    />
    <button v-on:click="searchDB" class="btn">
      Search
    </button>

    <MoviesTable :jsonDatabase="jsonFiltered"
                 :key="renderkey"/>
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
      renderkey: 0,
      jsonFiltered: lodash.cloneDeep(this.jsonDatabase),
      searchVal: {
        title: "",
      },
    }
  },

  methods: {

    isFilled: function (val) {
      return val === "";
    },

    getLowerCaseVal: function (val) {
     // console.log(lodash.toLower(val));
     // alert(lodash.toLower(val));
      return lodash.toLower(val);
    },

    isIncluded: function (array, input) {
      return (lodash.includes(this.getLowerCaseVal(array),
        this.getLowerCaseVal(input)))
    },

    checkInputs: function (item) {
      if (this.isIncluded(item.title, this.searchVal.title)) {
        return true;
      }
      console.log("checkInput false");
      return false;
    },

    isInputFilled: function () {
      if (!(this.isFilled(this.searchVal.title))) {
        alert("t");
        return true;
      }
      alert("f");
      return false;
    },

    searchDB: function () {
      this.jsonFiltered = [];

      if (this.isInputFilled()) {
         for (let movie in this.jsonDatabase) {
           if (this.checkInputs(this.jsonDatabase[movie])) {
             this.jsonFiltered.push(this.jsonDatabase[movie]);

           }
         }
      } else {
        this.jsonFiltered = lodash.cloneDeep(this.jsonDatabase);
      }
    this.renderkey = this.renderkey + 1;
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
