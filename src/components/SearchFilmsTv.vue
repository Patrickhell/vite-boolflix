<template>
    <header>
        <div class="col-10">
            <div class="row justify-content-around ">
              <div class="col-3 m-4 ">
                 <img src="https://image.tmdb.org/t/p/w92/wwemzKWzjKYJFfCeiB57q3r4Bcm.png" alt="">
              </div>
              <div class=" col-7 m-4 ">
                <div class="input-group " >
                    <input type="text" class="form-control" placeholder="Search Films o Series" aria-label="Search Films o Series" aria-describedby="button-addon2" v-model="SearchText" style="background-color: black; color: white;border-color:#282828 ;">
                    <button class="btn btn-outline-secondary" type="button" id="button-addon2" @click="$emit('searched',SearchText)">Search</button>
                </div>
              </div>
            </div>

        </div>
    </header>
    
</template>
 
 <script>

 export default {
     name: 'SearchFilmsTv',
     
     data(){
         return{
             SearchText:''
         }
     },

     methods: {
         logContent(content) {
             console.log(content)
         }
     },

 }
 </script>
 
 <style lang="scss" scoped>
 header{
    height:80px ;
    margin: 0 auto;
    background-color:#282828;
    opacity: .6;


 }
 
 </style>
 
 