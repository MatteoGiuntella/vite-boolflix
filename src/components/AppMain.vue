<script>
import axios from 'axios';
import {store} from '../store.js';
import Flagmain from './Flagmain.vue'
export default {
    data() {
        return {
            store,
        };
    },
    methods: { },
    components: {
        Flagmain,
    }
   
}
</script>

<template>
    <main>
       <div class="container">
        <h2>Movies</h2>

            <div class="container d-flex flex-wrap">
                    <div v-for="(elem) in this.store.movies" >
                        <Flagmain
                        :title=" elem.title" 
                        :originalTitle="elem.original_title "
                        :overview="elem.overview"
                        :objfilm="elem"
                        />
                    </div>
            </div>
        <h2>Series</h2>
        <div class="container d-flex flex-wrap">
                    <div v-for="(elem) in this.store.series">
                        <Flagmain
                        :title=" elem.name" 
                        :originalTitle="elem.original_name "
                        :overview="elem.overview"
                        :objfilm="elem"
                        />
                    </div>
            </div>
           
       </div>
    </main>
</template>

<style lang="scss" scoped>
main{
    background-color: black;
}
</style>
