<template>
    <article >
       
       <h2>  Titolo :{{ title }}</h2>
       <h2> Titolo Originale :{{original_title}}</h2>
       <h2> Lingua :{{ language }}</h2>
       <h2> voto :{{ vote_average }}</h2>
     

    </article>
</template>

<script>
export default {
    name: 'FilmElements',



    props: {
        title: String ,
        original_title: String,
        language: String,
        vote_average: Number
    },

}
</script>

<style lang="scss" scoped>

</style>