
<template>
    <main >
        <SearchFilmsTv @searched ="RequestSend"/>
        <div class="container pt-5 mb-5" >
            <div class="col-12">
                <h5 style="color:antiquewhite">FILMS NETFLIX</h5>
                <div class="row cards-content">
                    <div class="card col-2 p-0" v-for= "elements in filmsList" :key ="elements" >
                        <img :src="generateUrlImage(elements.poster_path)" alt="path_imageFilm" class="poster p-0" >
                        <div class="bodyCard p-2">
                            <p ><span> Titolo: </span>  {{elements.title}} </p>    
                            <p> <span> Titolo Originale:</span> {{elements.original_title}}</p> 
                            <div>
                                <span> Lingua Originale: </span>
                                <img  :src="getFlag(elements.original_language)" alt=" Flag image not found" 
                                style="width: 30px; color: brown;"> 
                            </div>
                           
                            <div class="d-flex">
                                <span> Vote:</span>
                                <div v-for="n in 5" :key="n">
                                  <i  class ="fa-star" :class="(n <= Math.trunc(Math.ceil(elements.vote_average/2))) ?'fa-solid' : 'fa-regular'"></i> 
                                </div>
                            </div>
                            <p>
                                <span>Overview:</span>
                                {{ elements.overview }}
                            </p>

                        </div>
                    </div>
                </div>
            </div>
        </div>
        <div class="container  " >
            <div class=" col-12 ">
                <h5 style="color:antiquewhite">SERIES NETFLIX</h5>
                <div class="row cards-content" >
                    <div class="card col-2 p-0" v-for= "seriesTv in tvList" :key ="seriesTv" >
                        <img :src="generateUrlImage(seriesTv.poster_path)" alt="path_imageSerie" class="poster p-0" > 
                        <div class="bodyCard p-2 ">
                            <p><span class="semibold"> Titolo :</span> {{seriesTv.name}}</p>    
                            <p><span> Titolo Originale:</span> {{seriesTv.original_name}}</p> 
                            <div>
                                <span> Lingua Originale:</span>
                                <img  :src="getFlag(seriesTv.original_language)" alt=" Flag image not found" 
                                style="width: 30px; color: brown;">
                            </div>
                           
                            <div class="d-flex">
                                <span > Vote:</span>
                                <div v-for="n in 5" :key="n">
                                  <i  class ="fa-star" :class="( n <= Math.trunc(Math.ceil(seriesTv.vote_average/2)))? 'fa-solid':'fa-regular'"></i> 
                                </div>
                            </div>
                            <p>
                                <span >Overview:</span>
                                {{ seriesTv.overview }}
                            </p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    
    </main>
    
    


    
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
            let imagesFlag = 'https://www.bandiere-mondo.it/data/flags/w702/' + initials_flag + '.webp';
               return imagesFlag
        },

        generateUrlImage(Pathposter) {

            let partialUrl = 'https://image.tmdb.org/t/p/w342' + Pathposter;
            return partialUrl

        },


       
    },

        create(){
            this.RequestSend()
           
        },
        
      

}
</script>

<style lang="scss" scoped>
main{
    background-color:#141922
}

.container{
    max-width: 1220px;
    margin: 0 auto;
    
}


ul{
    list-style-type: none;
}


.card{
    background-color:black;
    text-align: left;
    position: relative;
    overflow-y:auto ;
    

}

div img.poster{
    object-fit: cover;
     width: 100%;
     opacity: .7;
     height: auto;
    

   
}
span{
    font-size: 14px;
    color: white;
}
p{
    font-size: 12px;
    color: antiquewhite;
    

}
.fa-solid{
    color: goldenrod;
    font-size: 15px;

}
.fa-regular{
    color:aliceblue
}
.bodyCard{
    display: none;
   
}
div.card:hover .bodyCard{
    display: block;
    position: absolute;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  height: 100%;
  width: 100%;
  opacity: 1;
 
}
div.card:hover .poster{
    display: none;
}





</style>