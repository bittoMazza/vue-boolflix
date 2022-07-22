<template>
    <div class="py-5 scroll-style">
        <h2 class="text-white text-start">SERIE TV</h2>
        <div class="scrollmenu">
                <Card class="d-inline-block" v-for="series in searchedSeries" :key="series.id" 
                :listItem="series"
                />
        </div>
    </div>
</template>

<script>
import Card from "./Card.vue"
export default {
    props:{
        searchedSeries:Array,
    },
     components:{
        Card,
    },
}
</script>

<style lang="scss" scoped>
@import "../styles/variables.scss";
.scrollmenu {
  overflow-x: auto;
  white-space: nowrap;
}
</style>