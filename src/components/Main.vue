<template>
    <main class="container mt-5">

        <div class="d-flex flex-wrap">
            <Disc v-for="(disc,index) in discs" :key="index" />
        </div>

    </main>



</template>

<script>
import axios from "axios";
import Disc from "./Disc.vue";

export default {
    name :"Main",
    data: function(){
        return{
            discs:[]
        }
    },
    created: function(){
        axios   
            .get("https://flynn.boolean.careers/exercises/api/array/music")
            .then(
                res=>{
                    console.log(res)
                    this.discs = res.data.response;
                    this.discs.forEach(
                        (element) => {
                            if(!this.genres.include(element.genre)){
                                this.genres.push(element.genre);
                            }
                        }
                    );
                    this.$emit("genresReady", this.genres)
                }
            )
            .catch(
                err=>{
                    console.log(err)
                }
            );
    },

    components: {
        Disc
    }
}
</script>


<style lang="scss">

</style>