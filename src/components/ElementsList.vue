<template>
    <div>
        <div class="d-flex flex-wrap">
            <Card  v-for="(element,index) in searchedElements" :key="element.id" 
            :searchedListCast="searchedCast"
            :searchedCastIndex ="index"
            :listItem="element"
            />
        </div>      
     </div>
</template>

<script>
import Card from "./Card.vue"
export default {
     props:{
        searchedElements:Array,
        searchedCast:Array,
    },
    components:{
        Card,
    },
}
</script>

<style lang="scss" scoped>
@import "../styles/variables.scss";

</style>