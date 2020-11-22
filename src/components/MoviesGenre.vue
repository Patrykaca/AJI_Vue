<template>
    <div class="listWrapper">
      <br/>
      <h2>Films by genre</h2>
      <!--
        v-for="(index,val) in jsonData" :key="val"

        {{jsonData[val]}}
        -->
      
      <div class="accordion" id="accordion" 
        v-for="(index,val) in jsonData" :key="val">

        <div class="accordion-item">

          <h3 class="accordion-item-head">{{jsonData[val]}}</h3>
          <div accordion-item-body>
            {{jsonData[val]}}
          </div>

        </div>

      </div>
    </div>
    
</template>

<script>

export default {
  name: "MoviesGenreList",
  props: {
    jsonData: Array,
    jsonMovies: Array
  },

  data(){
    
    return this.jsonData
  },

  methods: {
  accordion: function (event) {            
 
        //Раскомментировать, если нужно, чтобы закрывались остальные пункты при открытии текущего
         var matches = document.querySelectorAll('.accordion-item-head');
         for(var i = 0; i < matches.length; i++) {
             matches[i].classList.remove('active');
          }
 
             event.target.classList.toggle('active');
  }}
}

</script>

<style lang="scss" scoped>

.listWrapper{
  margin-top: 20px;
  margin-left: 120px;
  margin-right: 120px;
  background-color: white;
  opacity: 0.8;
}

.accordion-item{
    position: relative;
}
 
.accordion-item-head{
    background-color: #dfdfdf;
    border-top-left-radius: 5px ;
    border-top-right-radius: 5px;
    cursor: pointer;
    padding:10px;
}
 
 
.accordion-item-head:after{    
    content: ' > ';
    display: block;
    height: 29px;
    position: absolute;
    right: 25px;
    transform: rotate(90deg) scaleY(2);
    top: 8px;
}
 
.accordion-item-head.active:after{
    content: ' < ';
}
 
 
.accordion-item-body{
    display: none;
} 
.accordion-item-head.active + .accordion-item-body{
    display: block !important;
}
</style>
