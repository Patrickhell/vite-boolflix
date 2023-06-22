
<template>
    <SearchFilms @searched ="RequestSend"/>   
    <div v-for= "elements in filmsList">
            <h3><strong>TITLE :</strong> {{elements.title}} </h3>    
            <h4><strong>ORIGINAL TITLE :</strong>{{elements.original_title}}</h4> 
            <div>
              <span><strong>LANGUAGE :</strong></span>
                <img  :src="getFlag(elements.original_language)" alt="FLAG IMAGE NOT FOUND" 
                style="width: 30px; color: brown;">
            
            </div> 
            <p><strong>VOTE AVERAGE :</strong>{{elements.vote_average}}</p> 
            
    </div>
</template>

<script>

import SearchFilms from './SearchFilms.vue';
import axios from 'axios';


export default {
    name: 'AppMenu',
    components:{
        SearchFilms,
    },
    
    data(){
        return{

            apiKey: 'de022abc3aaf072b21a84064d6a6134a',
            filmsList: [],
            IsFound: true,

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
        
        },

        getFlag(initials_flag) {
           
            if (initials_flag === 'en' ) initials_flag = 'gb'
            let images = 'https://www.bandiere-mondo.it/data/flags/w702/' + initials_flag + '.webp';
               return images
        },

        getImagePath: function(img) {
            return new URL(`../assets/img/${img}`, import.meta.url).href;
        
      }
        

       
    },

        create(){
            this.RequestSend()
           
        },
        
      

}
</script>

<style lang="scss" scoped>

</style>