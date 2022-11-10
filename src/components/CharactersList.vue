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
    <div class="row row-cols-5 gap-2">
        <div class="col" v-for="character in store.characters" :key="character.char_id">
            <AppCard  :character="character" />
        </div>
    </div>
</template>

<style lang="scss" scoped>
</style>