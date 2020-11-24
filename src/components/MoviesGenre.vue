<template>

    <div class="MoviesGenreList">
    <!-- v-for="(index, val) in tableSize" :key="val" -->
    <dl v-for="(index, val) in jsonData" :key="val" >
      <dt @click="changeState(val)">{{jsonData[val]}}</dt>
      <!--<dd v-show="genreState[val]"
      v-for="i in getGroup(val)" :key="i">{{i.title}}</dd>-->
      <div v-if="genreState[val]">
          <dd v-for="i in getGroup(val)" :key="i">{{i.title}}</dd>
          <!--<dd>Some text</dd>-->
      </div>
      
    </dl>

    </div>
    
</template>

<script>
import _ from 'lodash';
let genreState = []
let gen 


export default {
  props: {
    jsonData: Array,
    jsonMovies: Array
  },

  data(){

    for(let i=0; i<this.jsonData.length; i++){
      genreState.push(false)
    }
    return {genreState}
    
  },


  methods: {
    changeState: function(index){
      genreState[index] = ! genreState[index]
      console.log(genreState[index])
      this.$forceUpdate();
      //vm.$forceUpdate();
    },
    getGroup: function(index){
      gen = this.jsonData[index]
      console.log(gen)
      let some = _.filter(this.jsonMovies, function(o){return o.genres==gen})
      console.log(some)
      return some
    }

  }
  
}

</script>

<style lang="scss" scoped>

</style>
