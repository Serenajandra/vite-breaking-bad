<script>
import {store} from "../store";
import AppCard from "./AppCard.vue";

export default{
    name: "CharactersList",

    components:{ 
        AppCard
    },
    
    data(){
        return{
            store
        }
    }
}
</script>

<template>
    <div class="search_result">
        <h4>Found {{store.characters.length}} characters</h4>
    </div>
    <div class="row row-cols-6 gap-1">
        <div class="col" v-for="character in store.characters" :key="character.char_id">
            <AppCard  :character="character" />
        </div>
    </div>
</template>

<style lang="scss" scoped>
.row{
    justify-content: space-around;
}
</style>