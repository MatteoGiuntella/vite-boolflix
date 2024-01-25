<script>
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';
import AppFooter from './components/AppFooter.vue';
import axios from 'axios';
import {store} from './store'
export default {
    data() {
        return {
            store
        };
    },
    components: {
        AppHeader,
        AppMain,
        AppFooter
    }, 
    
    methods: {
        GetFilm (){
            axios.get('https://api.themoviedb.org/3/search/movie?api_key=83c77370d4de9a06185d3fa334f6fcc7',{
                params :{
                    query:this.store.searchText
                }
            })
            .then((response) =>{
            for (let i = 0; i < response.data.results.length; i++) {
                this.store.movies.push(response.data.results[i]) 
                
            }
            console.log(response)
            });
            axios.get('https://api.themoviedb.org/3/search/tv?api_key=83c77370d4de9a06185d3fa334f6fcc7',{
                paramas : {
                    query: this.store.searchText
                }
            })
            .then((response) =>{
            for (let i = 0; i < response.data.results.length; i++) {
                this.store.series.push(response.data.results[i])      
            }
            console.log(response)
            })
            
        },
    },
    created(){
        this.GetFilm()
    }
} 

</script>

<template>
    <AppHeader />

    <AppMain />

    <AppFooter />
</template>

<style lang="scss">
@use "assets/scss/main" as *;
@import "assets/scss/partials/reset";
</style>
