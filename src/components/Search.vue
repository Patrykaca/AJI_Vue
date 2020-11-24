<template>
  <div class="searchWrapper">
    <h1>Movies database</h1>
    <input
        class="inputClass"
        id="searchTitle"
        name="search"
        type="text"
        placeholder="Title"
        v-model="searchVal.title"
    />
    <input
        class="inputClass"
        id="searchCast"
        name="search"
        type="text"
        placeholder="Cast"
        v-model="searchVal.cast"
    />
    <input
        class="inputClass"
        id="searchDateFrom"
        name="search"
        type="text"
        placeholder="Date from"
        v-model="searchVal.dateFrom"
        min="1900"
        max="2100"
    />
    <input
        class="inputClass"
        id="searchDateTo"
        name="search"
        type="text"
        placeholder="Date to"
        v-model="searchVal.dateTo"
        min="1900"
        max="2100"
    />
    <button v-on:click="searchDB" class="btnClass">
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
        cast: "",
        dateFrom: "",
        dateTo: "",
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
      if (this.isIncluded(item.title, this.searchVal.title)
          && this.isIncluded(item.cast, this.searchVal.cast)) {
        return true;
      }
      console.log("checkInput false");
      return false;
    },

    isInputFilled: function () {
      if (!(this.isFilled(this.searchVal.title)
          && this.isFilled(this.searchVal.cast))) {
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
  margin: 10px;
}

.inputClass {
  margin-bottom: 10px;
  width: 350px;
  height: 30px;
  align-content: center;
  border-style: ridge;
  border-radius: 15px;
  transition: box-shadow 0.3s ease-in-out;
}

.inputClass:focus {
  -webkit-box-shadow: 0px 10px 16px -5px rgba(0,0,0,0.59);
  -moz-box-shadow: 0px 10px 16px -5px rgba(0,0,0,0.59);
  box-shadow: 0px 10px 16px -5px rgba(0,0,0,0.59);
}

.btnClass {
  width: 360px;
  height: 40px;
  align-content: center;
  margin-top: 15px;
  margin-bottom: 15px;
  border-radius: 15px;
  border-style: groove;
}


</style>
