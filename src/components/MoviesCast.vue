<template>
  <div>
    <h1 class="header" >Films by cast</h1>

    <dl class="list-item"  v-for="(index, val) in listSize" :key="val">

      <dt @click="changeState(val)">{{casts[val]}}</dt>
      <div v-if="castState[val]">
          <dd  class="list-item-body" 
          v-for="i in getCast(val)" :key="i">{{i.title}}</dd>
      </div>
      
    </dl>

    

  </div>
</template>

<script>
import _ from 'lodash';

let castSet = new Set()
let casts = []
let castState = []
let listSize
let cas

export default {
  name: "MoviesCast",
  props:{
    jsonData: Array
  },
  data(){
    for(let i in this.jsonData){
      castSet.add(this.jsonData[i].cast)
    }
    let castsArray = _.filter(Array.from(castSet),function(o){return Array.isArray(o) && o.length!=0})
    //casts = castsArray.join(", ")

    for(let i=0; i< castsArray.length; i++){
      if(Array.isArray(castsArray[i])){
        for(let j=0; j< castsArray[i].length; j++){
          casts.push(castsArray[i][j])
      }
      }
      else 
        casts.push(castsArray[i])
    }

    for(let i=0; i<casts.length; i++){
      castState.push(false)
    }
    listSize = 10
//    console.log(casts)
    return {casts,castState,listSize}
  },
  methods:{
    changeState: function(index){
      castState[index] = !castState[index]
      console.log(castState[index])
      this.$forceUpdate()
    },
    getCast: function(index){
      cas = casts[index]
      console.log(cas)
      for(let i in this.jsonData){
        if(this.jsonData[i].cast.includes(cas)){
          console.log('Cast exists')
        }
      }
      //let some = _.filter(this.jsonMovies, function(o){return o.genres==gen})
      let some = _.filter(this.jsonData, function(o){return o.cast.includes(cas)})
      console.log(some)
      return some
    }

  }
}
</script>

<style lang="scss" scoped>

.list-item{
    background-color: #fffefe;
    border-top-left-radius: 20px ;
    border-top-right-radius: 20px;
    padding:10px;
    margin-left: 120px;
    margin-right: 120px;
    opacity: 0.8;

}
 
.list-item-body{
    background-color: #dfdfdfcc;
    border-radius: 10px;
    padding:10px;
    margin-block: 15px;
    display: block;

}
.header{
    margin-left: 120px;
}
</style>
