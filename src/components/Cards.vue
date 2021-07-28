<template>
<div class="cards-container">
    <div class="cards-details">
        <div class="movie-poster" @mouseover="hover=true" @mouseleave="hover=false">
            <img :src='generateImg' alt="poster">
        </div>
        <div class="movie-details" v-if="hover" >
            <h5>{{ title }}</h5>
            <div class="original_launguage">
                Original Language: 
                <flag v-if="original_language == 'en'" iso="us" />
                <flag v-else :iso="original_language" />
            </div>  
            <div class="vote">Score: {{ vote_average}}</div>  
            <i v-for="i in 5" :key="i" class='fa-star' :class=" i <= voteRounded ? 'fas': 'far' "></i>
        </div>
    </div>
</div>
</template>



<script>


export default {
    name: 'Cards',
    props: {
        poster_path: String,
        title: String,
        original_title: String,
        original_language: String,
        vote_average: Number
    },
    computed:{
        generateImg(){
            return 'https://image.tmdb.org/t/p/w342' + this.poster_path 
        }
    },
    data(){
        return{
            hover:false,
            voteRounded: Math.round(this.vote_average / 2)
        }    
        
    }
}
</script>


<style lang="scss" scoped>

.cards-container{
    margin:30px 25px;
    position: relative;
    max-width: 320px;


    .movie-details{
        width: 342px;
        text-align: center;
        color:rgb(255, 255, 255);
        position: absolute;
        bottom:150px;
        background-color: rgba(96, 97, 99, 0.658);
    }






}


</style>