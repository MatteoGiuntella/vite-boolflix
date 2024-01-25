<script>
import axios from "axios";
import { store } from "../store.js";
export default {
  data() {
    return {
      store,
    };
  },
  methods: {GetFilm (){
    axios.get('https://api.themoviedb.org/3/search/movie?api_key=83c77370d4de9a06185d3fa334f6fcc7',{
                params :{
                    query:this.store.searchText
                }
            })
            .then((response) =>{

                this.store.movies = response.data.results

            console.log('film',this.store.movies)
            });

            axios.get('https://api.themoviedb.org/3/search/tv?api_key=83c77370d4de9a06185d3fa334f6fcc7',{
                params :{
                    query:this.store.searchText
                }
            })
            .then((response) =>{

                this.store.series = response.data.results
                console.log('response',response.data)
                console.log('series',this.store.series)
            });            
        },
      },
};
</script>

<template>
  <header>
    <div class="search-bar d-flex justify-content-between container-fluid bg-black ">
      <div class="container-img">
        <img src="../assets/img/BrandAssets_Logos_01-Wordmark.jpg" alt="" />
      </div>
      <div class="bar">
        <form class="d-flex" role="search">
          <input
            v-model="store.searchText"
            class="form-control me-2"
            type="search"
            placeholder="Search..."
            aria-label="Search"
          />
          <button @click="GetFilm()" class="btn btn-outline-success" type="button">Search</button>
        </form>
      </div>
    </div>
  </header>
</template>

<style lang="scss" scoped>
.search-bar{
    padding: 20px;
}
.container-img {
  width: 200px;
  height: 50%;
  img {
    height: 50px;
    width: 100%;
  }
}
</style>
