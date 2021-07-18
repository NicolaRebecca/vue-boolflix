<template>
    
    <div class="container">
        <div class="row">
            <Cards class="cover" 
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
        cards: Array
    }
}
</script>


<style lang="scss">


</style>
