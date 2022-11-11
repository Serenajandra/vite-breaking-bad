<script>
export default {
    name: "AppCard",

    props: {
        character: Object
    }
}
</script>

<template>
 
        <div class="card">
            <div class="card_container">
                <img :src="character.img" alt="">
            </div>
                <h4>{{character.name}}</h4>
            <p>Role</p>
        </div>


</template>

<style lang="scss" scoped>
@use "../styles/partials/variabiles";
.card{
    background-color:  rgba(33, 37, 41, 1);
    color: white;

    .card_container{
        img{
            object-fit: contain;
        }
    }
}

</style>