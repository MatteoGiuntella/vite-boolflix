<script>
import axios from 'axios';
import {store} from '../store.js'
export default {
    data() {
        return {
            store,
        };
    },
    props: {
        title : String,
        originalTitle : String,
        vote : Number,
        originalLanguage : String,
        overview : String,
        objfilm : Object,
    },
    methods:{
        flagfilm (){
            this.objfilm.original_language= this.objfilm.original_language.toUpperCase()
            if(this.objfilm.original_language == 'EN'){
                this.objfilm.original_language = 'GB'
            }
            else if(this.objfilm.original_language == 'JA') {
                this.objfilm.original_language = 'JP'
            }
            else if(this.objfilm.original_language == 'KO') {
                this.objfilm.original_language = 'KR'
            }
            console.log(this.objfilm.original_language)
        }
    },
    mounted(){
        this.flagfilm()
    }
   
}
</script>

<template>
    <div class="imgContainer">
        <img :src="'https://image.tmdb.org/t/p/w342/'+ this.objfilm.poster_path" :alt="this.objfilm.poster_path">
    </div>
    <h5>Title: {{ title }} </h5>
    <h4>Original title: {{ originalTitle }} </h4>
    <h4>Vote: {{ vote }} </h4>
    <span>Original language: <img :src="'https://flagsapi.com/'+ objfilm.original_language + '/flat/64.png'" :alt="objfilm.original_language"> </span>
    <p>Overview: {{ overview }} </p>
</template>


<style lang="scss" scoped>
.imgContainer{
    width: 50px;
    height: 150px;
}
</style>
