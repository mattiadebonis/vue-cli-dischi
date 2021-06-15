<template>
    <header class="d-flex justify-content-between px-3">
        <div>
            <img src="../assets/img/spotify.png" alt="Logo Spotify">
        </div>
        <div>
            
            <select 
                value=""
                v-model="selectedGenre"
                @change= "$emit('changedGenre',selectedGenre)"
            >
                <option value="">Seleziona un genere</option>
                <option 
                    v-for="(genre, index) in genres" 
                    :key="index"
                    :value="genre"
                >
                    {{ genre }}    
                </option>
            </select>
        </div>

    </header>


</template>


<script>

export default {
    name: "Header",
    props:{
        "genres" : Array,
    }
}

</script>

<style lang="scss">
    @import "../assets/styles/variables";

    header{
        height: 70px;
        line-height: 70px;
        background-color: $light-color;

        img{
            width: 50px;

        }
        
        select{
            padding: 5px;
        }
    }

</style>
