<script>
export default {
    name: "AppCard",

    props: {
        character: Object
    }
}
</script>

<template>
 
    <div class="ms_card">
        <div class="card_container">
            <img :src="character.img" alt="">
        </div>
        <p class="mt-1">{{character.name}}</p>
        <p class="fst-italic fw-lighter">{{character.status}}</p>
       
    </div>


</template>

<style lang="scss" scoped>
@use "../styles/partials/variabiles";
.ms_card{
    background-color:  rgba(33, 37, 41, 1);
    color: white;
    padding: 1rem;
    height: 21rem;

    .card_container{
        width: 90%;
        height: 70%;
        margin: 0 auto;
        img{
            object-fit: contain;
        }
    }
}

</style>