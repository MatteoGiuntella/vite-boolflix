<script>
import axios from 'axios';
import {store} from '../store.js'
export default {
    data() {
        return {
            store,
        };
    },
    methods: {
        getFlag(stringa){
           stringa = stringa.toUpperCase()
           if(stringa == 'EN'){
            stringa = 'GB'
           }
        }
        
    },
   
}
</script>

<template>
    <main>
       <div class="container">
        <h2>Film</h2>
            <ul v-for="(elem) in store.movies">
                <li>Title: {{ elem.title }} </li>
                <li>Original title: {{ elem.original_title }} </li>
                <li>Vote: {{ elem.vote_average }} </li>
                <li>Original language: {{ elem.original_language }} </li>
                <li>Overview: {{ elem.overview }} </li>
                <img :src="'https://flagsapi.com/'+ getFlag(elem.original_language) + '/flat/64.png'" alt="">
            </ul>
        <h2>Serie</h2>
            <ul v-for="(elem) in store.series">
                <li>Title: {{ elem.name }} </li>
                <li>Original title: {{ elem.original_name }} </li>
                <li>Vote: {{ elem.vote_average }} </li>
                <li>Original language: {{ elem.original_language }} </li>
                <li>Overview: {{ elem.overview }} </li>
                <img :src="'https://flagsapi.com/'+ elem.original_language + '/flat/64.png'" alt="">
            </ul>
       </div>
    </main>
</template>

<style lang="scss" scoped>

</style>
