<template>
    <div class="input-group my-4 mx-4 " style="width: 400px;">
       <input type="text" class="form-control" placeholder="Search Film" aria-label="Search Film" aria-describedby="button-addon2" v-model="SearchText">
       <button class="btn btn-outline-secondary" type="button" id="button-addon2" @click="$emit('searched',SearchText)">VAI</button>
    </div>
    
 </template>
 
 <script>
 
 export default {
     name: 'SearchFilms',
     
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
 
 