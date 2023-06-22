
<template>
    <SearchFilmsTv @searched ="RequestSend"/>
    <div class="col-12">
        <div class="row">
            <div class="col-6" v-for= "elements in filmsList">
              <h3><strong> FILM Title :</strong> {{elements.title}} </h3>    
              <h4><strong>ORIGINAL Title FILM :</strong>{{elements.original_title}}</h4> 
              <div>
                <span><strong> FILM Language :</strong></span>
                <img  :src="getFlag(elements.original_language)" alt="FLAG IMAGE NOT FOUND" 
                style="width: 30px; color: brown;">
              </div> 
              <p><strong> FILM Vote Average :</strong>{{elements.vote_average}}</p> 
            </div>

            <div class="col-6" v-for= "seriesTv in tvList">
              <h3><strong>Serie Title :</strong> {{seriesTv.name}} </h3>    
              <h4><strong>ORIGINAL Title Serie :</strong>{{seriesTv.original_name}}</h4> 
              <div>
                <span><strong> SERIE Language  :</strong></span>
                <img  :src="getFlag(seriesTv.original_language)" alt="FLAG IMAGE NOT FOUND" 
                style="width: 30px; color: brown;">
              </div> 
              <p><strong> Serie Vote Average :</strong>{{seriesTv.vote_average}}</p> 
            </div>

        </div>
        
    </div> 
       
        
</template>

<script>

import SearchFilmsTv from './SearchFilmsTv.vue';
import axios from 'axios';


export default {
    name: 'AppMenu',
    components:{
        SearchFilmsTv,
    },
    
    data(){
        return{

            apiKey: 'de022abc3aaf072b21a84064d6a6134a',
            filmsList: [],
            tvList:[],

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

            axios.get(`https://api.themoviedb.org/3/search/tv?api_key=${this.apiKey}&query=${needle}&language=it-IT`)
            .then((response)=> {
            console.log(response.data.results);
            this.tvList = response.data.results ;
            
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

       
    },

        create(){
            this.RequestSend()
           
        },
        
      

}
</script>

<style lang="scss" scoped>

</style>