<script>
import axios from 'axios';
import {store} from '../store.js'
export default {
    data() {
        return {
            store
        };
    },
    methods: {

    }
}
</script>

<template>
    <main>
       <div>
        <h2>film</h2>
            <ul v-for="(elem) in store.movies">
                <li>Title: {{ elem.title }}</li>
                <li>Original title: {{ elem.original_title }}</li>
                <li>Vote: {{ elem.vote_average }}</li>
                <li>Original language: {{ elem.original_language }}</li>
                <li>Overview: {{ elem.overview }}</li>
            </ul>
       </div>
       <div>
        <h2>serie</h2>
            <ul v-for="(elem,i) in store.series">
                <li>Title: {{ elem.title }}</li>
                <li>Original title: {{ elem.original_title }}</li>
                <li>Vote: {{ elem.vote_average }}</li>
                <li>Original language: {{ elem.original_language }}</li>
                <li>Overview: {{ elem.overview }}</li>
            </ul>
       </div>
    </main>
</template>

<style lang="scss" scoped>

</style>
