<template>
  <div>
    <h2 class="text-white">Serie</h2>
    <Card
    :seriesList="searchedSeries"
    />
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