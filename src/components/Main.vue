<template>
    <main class="container mt-5">

        <div class="d-flex flex-wrap">
            <Disc
                v-for="(disc,index) in filteredDiscs "
                :key="index"
                :item= "disc"
            />
            
        </div>

    </main>



</template>

<script>
import axios from "axios";
import Disc from "./Disc.vue";

export default {
    name :"Main",
    props: {
        "selectedGenre": String

    },
    data: function(){
        return{
            discs:[],
            genres :[]
        }
    },
    created: function(){
        axios   
            .get("https://flynn.boolean.careers/exercises/api/array/music")
            .then(
                res=>{
                    this.discs = res.data.response;
                    this.discs.forEach(
                        (element) => {
                            
                            if(!this.genres.includes(element.genre)){
                                this.genres.push(element.genre);
                            }
                        }
                    );
                    this.$emit("genresReady", this.genres);                  
                }
            )
            .catch(
                err=>{
                    console.log(err)
                }
            );
    },
    computed:{
        filteredDiscs : function(){
            if(this.selectedGenre == ""){
                return this.discs;
            }

            return this.discs.filter(
                element => element.genre == this.selectedGenre
            );
        }
    },
    components: {
        Disc
    }
}
</script>


<style lang="scss">

</style>