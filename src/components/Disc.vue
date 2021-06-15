<template>
    <div class="disc p-3 text-center mb-4">
        
        <img :src="item.poster" :alt="item.title" class="mb-3">
        <h2>{{ item.title }}</h2>
        <h3>{{ item.autor}}</h3>
        <h3>{{ item.year}}</h3>
    </div>
</template>


<script>
export default {
    name : "Disc",
    props: {
        item : Object
    }
}
</script>

<style lang="scss">
    @import "../assets/styles/variables";

    .disc{
        width: calc(100%/5);
        background-color: $light-color;
        color: white;
        margin:  20px;
        
        img{
            width: 200px;
        }
        h2{
            font-size: 22px;
        }
        h2{
            font-size: 18px;
        }
    }

</style>