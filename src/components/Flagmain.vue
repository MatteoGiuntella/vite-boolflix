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
        },
        decimalvote(){
            this.objfilm.vote_average = Math.round(this.objfilm.vote_average / 2)

            console.log(this.objfilm.vote_average)
        }
    },
    update(){
        this.flagfilm()
        this.decimalvote()
    },
    mounted(){
        this.flagfilm()
        this.decimalvote()
    }
   
}
</script>

<template>
    <div class="imgContainer">
        <img :src="'https://image.tmdb.org/t/p/w342/'+ this.objfilm.poster_path" :alt="this.objfilm.poster_path">
    </div>
    <h3>Title: {{ title }} </h3>
    <h4>Original title: {{ originalTitle }} </h4>
    <h4>Vote: {{ objfilm.vote_average }} <i v-for="(elem,i) in 5" :key="i"  class="fa-solid fa-star fullstar" :class="{blackflag: objfilm.vote_average <= i}"></i></h4>
    <span>Original language: <img :src="'https://flagsapi.com/'+ objfilm.original_language + '/flat/64.png'" :alt="objfilm.original_language"> </span>
    <p>Overview: {{ overview }} </p>
</template>


<style lang="scss" scoped>
.imgContainer{
    width: 50px;
    height: 150px;
}
.fullstar{
    color: yellow;
}
.blackflag{
    color: black;
}
</style>
