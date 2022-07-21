<template>
  <header>
    <div class="search-container p-3">
        <input type="text" v-model="searchedElement" @keyup.enter="$emit('selectElement',searchedElement)" placeholder="Scrivi quale film vuoi cercare">
        <button @click="$emit('selectElement',searchedElement)"> CERCA </button>
    </div>
  </header>
</template>

<script>
export default {
    data:function(){
        return{
            searchedElement:'',
        }   
    },
}
</script>

<style lang="scss">

</style>