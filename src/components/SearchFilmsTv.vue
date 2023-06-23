<template>
    <div class="d-flex justify-content-center">
        <div class="input-group my-4 mx-4 " style="width: 600px;">
          <input type="text" class="form-control" placeholder="Search Film" aria-label="Search Films o Series" aria-describedby="button-addon2" v-model="SearchText">
          <button class="btn btn-outline-secondary" type="button" id="button-addon2" @click="$emit('searched',SearchText)">VAI</button>
        </div>
    </div>
    
    
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
     }
 
 }
 </script>
 
 <style lang="scss">
 
 </style>
 
 