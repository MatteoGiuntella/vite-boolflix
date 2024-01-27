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
    <div class="card mx-3 my-3 ">
        <div class="box-poster">
             <img :src="'https://image.tmdb.org/t/p/w342/'+ this.objfilm.poster_path" :alt="this.objfilm.poster_path">
        </div>
        <div class="box-information p-2">
            <span> <h3>Title: {{ title }} </h3> </span>
            <span> <h4>Original title: {{ originalTitle }} </h4>  </span>
            <span> <h4>Vote: {{ objfilm.vote_average }} <i v-for="(elem,i) in 5" :key="i"  class="fa-solid fa-star fullstar" :class="{blackflag: objfilm.vote_average <= i}"></i></h4> </span>
            <h4>Original language: <img class="flag" :src="'https://flagsapi.com/'+ objfilm.original_language + '/flat/64.png'" :alt="objfilm.original_language"> </h4> 
            <span> <h5>Overview:</h5> <p> {{ overview }} </p></span>
        </div>
    </div>
</template>


<style lang="scss" scoped>
.card{
    // max-width: 341px;
    min-height: 474px;
    border: 0px solid black;
    background-color: black;
    position: relative;
    .box-poster{
        // display: block;
        .imgContainer{
         width: 100%;
         border: 0px solid black;
        border-radius: 20px; 
    }
    }
    &:hover .box-information{
        display: block;
    }
    
    .box-information{
        display: none;
        color: white;
        background-color: black;
        position: absolute;
        top: 0%;
        left: 0%;
        width: 100%;
        height: 100%;
        overflow: auto;
       
        span{
            .flag{
                display: inline-block;
            }
        }
   
    }
    &:hover{
        display: block;
        border: 1px solid #E30913;
    }

}

.fullstar{
    color: yellow;
}
.blackflag{
    color: black;
}
</style>
