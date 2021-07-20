<template>
    
    
    <div class="container">
        <div class="row ">
            <a name="movie"></a>
            <h3>Film più popolari</h3>
            <Cards class="cover col" 
            v-for=" cards in cards" :key="cards.id" 
            :poster_path="cards.poster_path" 
            :title="cards.title" 
            :original_title="cards.original_title" 
            :original_language="cards.original_language" 
            :vote_average="cards.vote_average" />
        </div>



        <div class="row">
            <a name="tv"></a>
            <h3>Serie TV più popolari</h3>
            <Tv class="cover col" 
            v-for="tvshow in tvshow" :key="tvshow.id" 
            :poster_path="tvshow.poster_path" 
            :original_name="tvshow.original_name" 
            :original_language="tvshow.original_language" 
            :vote_average="tvshow.vote_average" />
        </div>
    </div>

</template>


<script>
import Cards from "../components/Cards.vue";
import Tv from "../components/Tv.vue";

export default {
    name: 'Main',
    components: {
        Cards,
        Tv
    },
    props:{
        cards: Array,
        filteredMovies: Array,
        tvshow: Array
    }
}
</script>


<style lang="scss">

.container{
    max-width: 100%;
    height: 100vh;
    overflow-y:scroll;
    background-color:rgb(77, 75, 75)
}

h3{
    padding-top:15px;
    color:white;
}



</style>
