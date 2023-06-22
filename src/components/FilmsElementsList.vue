<template>
    <div>
        <FilmElements v-for =" elements in filmsList"
              :title ='elements.title'
              :original_title ='elements.original_title'
              :language ='elements.original_language'
              :vote_average ='elements.vote_average' />
    </div>
   
 
</template>

<script>
import FilmElements from './FilmElements.vue';

export default {
    name: 'FilmsElementsList',
    data(){
        return{

        }
    },

    components:{
        FilmElements,
    },

    props: {
        filmsList: Array,
    }

}
</script>

<style>

</style>