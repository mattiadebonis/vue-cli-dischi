<template>
  <main class="container mt-4">
      <div class="d-flex flex-wrap">
        <Disc 
          v-for="(disc, index) in filteredDiscs"
          :key="index"
          :item="disc"
        />
      </div>
  </main>
</template>

<script>
import Disc from './Disc';
import axios from 'axios';
export default {
    name: "Main",
    props: {
      selectedGenre: String,
      selectedAuthor: String
    },
    data: function() {
      return {
        discs: [],
        genres: [],
        authors: [],
      }
    },
    created: function() {
      axios
        .get('https://flynn.boolean.careers/exercises/api/array/music')
        .then(
          res => {
            // console.log(res);
            this.discs = res.data.response;
            this.discs.forEach(
              (element) => {
                // popoliamo l'array genres
                if(!this.genres.includes(element.genre)) {
                  this.genres.push(element.genre);
                }
                // popoliamo l'array authors  
                if(!this.authors.includes(element.author)) {
                  this.authors.push(element.author);
                }
              }
            );
            
            this.$emit('dataReady', this.genres, this.authors);
            this.loading = false;
          }
        )
        .catch(
          err => {
            console.log(err);
          }
        );
    },
    computed: {
      filteredDiscs: function() {
        if(this.selectedGenre == "" && this.selectedAuthor == "") {
          return this.discs;
        } else if(this.selectedAuthor != "") {
          return this.discs.filter(
            element => element.author == this.selectedAuthor
          );
        }
        return this.discs.filter(
          element => element.genre == this.selectedGenre
        );
      }
    },
    components: {
      Disc,
    }
}
</script>


<style lang="scss">

</style>