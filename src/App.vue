<script>
  import axios from "axios";
  import {store} from "./store";
  import AppCard from "./components/AppCard.vue";
  import CharactersList from "./components/CharactersList.vue";
  
  export default {
    components:{ 
      AppCard,
      CharactersList,
    
    },
    data(){
      return{
        store
      }
    },
    created() {
      axios.get("https://www.breakingbadapi.com/api/characters").then((resp => {
        this.store.characters = resp.data;
        // console.log(this.store.characters)
            }))

    }
  }
</script>

<template>
  <div class="flex-container ms_container">
    <header class=" ms_header">
      <h1 class="text-light">Breaking Bad Api</h1>
      
    </header>  

    <main>
      <div class="top_menu">
        <p class="text-light">Select category</p>
      </div>
      <div class="container bg-light">
        <div class="search_result">
          <h4>Found 62 characters</h4>
        </div>
        <div class="container">
          <CharactersList />
          <!-- <AppCard /> -->
        </div>

      </div>
    </main>
    
  </div>

</template>

<style lang="scss">
@use "./styles/general.scss" as*;
@use "./styles/partials/_variabiles.scss" as*;

.ms_container{
  background-color: rgba(33, 37, 41, 1);
  width: 100%;
  

  .ms_header{
    width: 100%;
    height: 60px;
    padding-left: 6rem;
  }

  .top_menu{
    padding-left: 11rem;
  }

  main{
    width: 100%;
    
  
    .container{
      width: 70%;

      margin: 0 auto;
      padding-top: 3rem;

      .search_result{
        background-color: rgba(33, 37, 41, 1);
        h4{
          color: white;
          padding: 1rem;
         }
        
      }
    }  
  }
}
</style>
