<template>
        <div class="carousel">
            <Card  v-for="(element,index) in searchedElements" :key="element.id" 
            :searchedListCast="searchedCast"
            :searchedCastIndex ="index"
            :listItem="element"
            :genreListElement="genreList"
            />
        </div>      
</template>

<script>
import Card from "./Card.vue"
export default {
     props:{
        searchedElements:Array,
        searchedCast:Array,
        genreList:Array,
    },
    components:{
        Card,
    },
}
</script>

<style lang="scss" scoped>
@import "../styles/variables.scss";
    ::-webkit-scrollbar {
        width: 12px;
    }

    ::-webkit-scrollbar-track {
        -webkit-box-shadow: inset 0 0 6px rgba(245, 19, 19, 0.3); 
        border-radius: 10px;
    }

    ::-webkit-scrollbar-thumb {
        border-radius: 10px;
        background:whitesmoke; 
    }
.carousel{
    overflow-x: scroll;
    overflow-y: hidden;
    white-space: nowrap;
}
</style>