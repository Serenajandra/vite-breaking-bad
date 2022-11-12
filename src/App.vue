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
        store,
        serie:"",
      }
    },

    methods: {
      toSelectSerie(event){
        // console.log("serie scelta");
        this.serie = event.target.value;

        axios.get(`https://www.breakingbadapi.com/api/characters?category=${this.serie}`).then((resp => {
           this.store.characters= resp.data;
           
          //  console.log(this.store.characters)
        }))
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
      <img src="./assets/img/logo (1).png" alt="">
      <h1 class="text-light">Breaking Bad Api</h1>
    </header>  

    <main>
      <section>
        <div class="top_menu">
          
          <select @change="toSelectSerie($event)" class="form-select m-3 mx-auto" name="" >
            <option value="Select-serie">Select serie</option>
            <option value="Breaking+Bad">Breaking bad</option>
            <option value="Better+Call+Saul">Better call Saul</option>
          </select>
  
        </div>
      </section>
      
      <section class="ms_small-container container-flex">
        <div class="container-flex margin_auto text-center">
          <CharactersList />
        </div>
      </section>
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
    padding-left: 2rem;
    padding-top: 1rem;
    display: flex;

    img{
      width: 4rem;
      margin-right: 2rem;
    }
  }

  main{
    width: 100%;
    .top_menu{
      padding: 2rem;
      width: 20rem;
      margin-left: 10rem;   
    }
    .ms_small-container{
      width: 80%;
      background-color: white;
      margin: 0 auto;
      padding-top: 3rem;

      .search_result{
        background-color: rgba(33, 37, 41, 1);
        width: 97%;
        margin: 0 auto;
        h4{
          color: white;
          padding: 1rem;
        }
        
      }
    }  
  }
}
</style>
