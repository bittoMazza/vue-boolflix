<template>
  <div>
    <h2>Serie</h2>
    <Card/>
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