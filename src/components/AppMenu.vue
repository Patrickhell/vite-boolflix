
<template>
    <SearchFilms @searched ="RequestSend"/>   
    <FilmsElementsList :filmsList="filmsList"/>
</template>

<script>

import SearchFilms from './SearchFilms.vue';
import axios from 'axios';
import FilmsElementsList from './FilmsElementsList.vue';

export default {
    name: 'AppMenu',
    components:{
        SearchFilms,
        FilmsElementsList,
    },
    
    data(){
        return{

            apiKey: 'de022abc3aaf072b21a84064d6a6134a',
            filmsList: [],
        }
    },

    methods:{
        RequestSend(needle='') {

            axios.get(`https://api.themoviedb.org/3/search/movie?api_key=${this.apiKey}&query=${needle}&language=it-IT`)
            .then((response)=> {
            console.log(response.data.results);
            this.filmsList = response.data.results ;
            
                
            })

               .catch(function (error) {
               console.log(error);
            })
        
            
           
        }
    },

        create(){
            this.RequestSend()
           
        }
      

}
</script>

<style lang="scss" scoped>

</style>