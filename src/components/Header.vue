<template>
  <header>
    <div class="d-flex justify-content-between align-items-center">
      <div>
        <img src="https://image.tmdb.org/t/p/w342/wwemzKWzjKYJFfCeiB57q3r4Bcm.png" class="netflix-logo m-3" alt="">
      </div>
      <div class="search-container p-3">
          <input type="text" class="" v-model="searchedElement" @keyup.enter="$emit('selectElement',searchedElement)" placeholder="Scrivi quale film vuoi cercare">
          <button @click="$emit('selectElement',searchedElement)"> CERCA </button>
      </div>
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
  header{
    background-color: black;
    .netflix-logo{
      width:100px;
    }
  }
</style>