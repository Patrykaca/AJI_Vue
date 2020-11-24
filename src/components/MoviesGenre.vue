<template>

    <div class="MoviesGenreList">
    <!-- v-for="(index, val) in tableSize" :key="val" -->
    <dl v-for="(index, val) in jsonData" :key="val" >
      <dt @click="changeState(val)">{{jsonData[val]}}</dt>
      <dd v-show="genreState[val]"> Here is some text</dd>
    </dl>

    </div>
    
</template>

<script>
//import _ from 'lodash';
let genreState = []


export default {
  props: {
    jsonData: Array,
    jsonMovies: Array
  },

  data(){

    for(let i=0; i<this.jsonData.length; i++){
      genreState.push(false)
    }
    genreState[0]=true

    genreState[3]=true
    return {genreState}
    
  },


  methods: {
    changeState: function(index){
      genreState[index] = ! genreState[index]
      console.log(genreState[index])
      this.$forceUpdate();
      //vm.$forceUpdate();
    },

  }
  
}

</script>

<style lang="scss" scoped>

</style>
