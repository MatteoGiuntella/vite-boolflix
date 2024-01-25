<script>
import axios from "axios";
import { store } from "../store.js";
export default {
  data() {
    return {
      store,
    };
  },
  methods: {},
};
</script>

<template>
  <header>
    <div class="searchbar d-flex justify-content-between container-fluid bg-black ">
      <div class="container-img">
        <img src="../assets/img/BrandAssets_Logos_01-Wordmark.jpg" alt="" />
      </div>
      <div class="bar">
        <form class="d-flex" role="search">
          <input
            class="form-control me-2"
            type="search"
            placeholder="Search..."
            aria-label="Search"
          />
          <button class="btn btn-outline-success" type="submit">Search</button>
        </form>
      </div>
    </div>
  </header>
</template>

<style lang="scss" scoped>
.searchbar{
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
