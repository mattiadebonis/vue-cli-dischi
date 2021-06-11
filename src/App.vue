<template>
  <div id="app">
    <Header :genres="allGenres" />    
    <Main @genresReady="setGenres" />


  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Main from "./components/Main.vue";

export default {
  name: 'App',
  data: function(){
    return {
      allGenres: []
    }

  },
  methods:{
    setGenres: function(array){
      this.allGenrs = array;
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
