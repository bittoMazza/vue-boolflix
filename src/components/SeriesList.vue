<template>
  <div>
    <h2 class="text-white text-center">Serie</h2>
    <div class="d-flex flex-wrap">
            <Card v-for="series in searchedSeries" :key="series.id" 
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

<style>

</style>