<template>
    
    <div class="container-fluid">
        <div class="row">
            <h3>I più popolari</h3>
            <Cards class="cover col" 
            v-for=" cards in cards" :key="cards.id" 
            :poster_path="cards.poster_path" 
            :title="cards.title" 
            :original_title="cards.original_title" 
            :original_language="cards.original_language" 
            :vote_average="cards.vote_average" />
                
        </div>
    </div>

</template>


<script>
import Cards from "../components/Cards.vue";
export default {
    name: 'Main',
    components: {
        Cards
    },
    props:{
        cards: Array,
        filteredMovies: Array
    }
}
</script>


<style lang="scss">

.row{
    height: 100vh;
    overflow-y:scroll;
    background-color:rgb(77, 75, 75)
}

h3{
    padding-top:15px;
    color:white;
}



</style>
