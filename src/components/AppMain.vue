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

            <div class="container">
                <ul>
                    <li v-for="(elem) in this.store.movies">
                        <Flagmain
                        :title=" elem.title" 
                        :originalTitle="elem.original_title "
                        :vote="elem.vote_average "
                        :overview="elem.overview"
                        :objfilm="elem"
                        />
                    </li>
                </ul>
            </div>
        <h2>Series</h2>
        <div class="container">
                <ul>
                    <li v-for="(elem) in this.store.series">
                        <Flagmain
                        :title=" elem.name" 
                        :originalTitle="elem.original_name "
                        :vote="elem.vote_average "
                        :overview="elem.overview"
                        :objfilm="elem"
                        />
                    </li>
                </ul>
            </div>
           
       </div>
    </main>
</template>

<style lang="scss" scoped>

</style>
