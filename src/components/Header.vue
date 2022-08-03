<template>
  <header>
    <div class="d-flex justify-content-between align-items-center px-3">
      <div class="d-flex align-items-center">
        <img src="https://image.tmdb.org/t/p/w342/wwemzKWzjKYJFfCeiB57q3r4Bcm.png" class="netflix-logo m-3" alt="">
        <nav class="mx-3">
          <ul class="text-white">
            <li>Home</li>
            <li>Serie Tv</li>
            <li>Film</li>
          </ul>
        </nav>
      </div>
      
      <div class="search-box p-3">
        <input type="text" class="input-search" v-model="searchedElement" @keyup.enter="$emit('selectElement',searchedElement)"  placeholder="Cosa vuoi guardare ?">
        <button class="btn-search" @click="$emit('selectElement',searchedElement)"><i class="bi bi-search"></i></button>
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
@import "../styles/variables.scss";
  header{
    background-color: black;
    position: fixed;
    width: 100%;
    top: 0;
    left: 0;
    z-index: 100;
    nav ul{
      padding: 0;
      margin: 0;
    }
    ul li{
      display: inline-block;
      list-style: none;
      padding: 10 10px;
      margin: 0 10px;
      font-size: 18px;
    }
    .netflix-logo{
      width:150px;
    }

.input-search{
  width: fit-content;
  border-style: none;
  padding: 8px;
  margin-right: 20px;
  font-size: 18px;
  letter-spacing: 2px;
  border-bottom: 1px solid white;
  background-color: black;
  color:#fff;

  &::placeholder{
  color:rgba(255,255,255,.5);
  font-size: 18px;
  letter-spacing: 2px;
  font-weight: 100;
  }
}

.btn-search{
  width: 50px;
  height: 50px;
  border-style: none;
  font-size: 20px;
  outline: none;
  border-radius: 50%;
  background-color:$mainColor;
  color:white ;
}
  }
</style>