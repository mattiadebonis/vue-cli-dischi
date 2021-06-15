<template>
  <div id="app">
    <Header 
      :genres="allGenres"
      @changedGenre = "updateSelectedGenre"
      
    />    
    <Main 
      :selectedGenre="currentGenre"   
      @genresReady="setGenres"  
    />


  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Main from "./components/Main.vue";

export default {
  name: 'App',
  data: function(){
    return {
      allGenres: [],
      currentGenre: []
    }

  },
  methods:{
    setGenres: function(array){
      this.allGenres = array;
      console.log(this.allGenres)
    },

    updateSelectedGenre: function(newGenre){
      this.selectedGenre = newGenre;
      
    }



  },
  components: {
    Header,
    Main
  }
}
</script>

<style lang="scss">
@import "./assets/styles/general.scss";
</style>
