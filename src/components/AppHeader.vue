<script>
import axios from "axios";
import { store } from "./store.js";
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
    <div class="navbar">
      <nav class="navbar bg-body-tertiary">
        <div class="container-fluid">
          <div class="container-img">
            <img src="" alt="">
          </div>
          <form class="d-flex" role="search">
            <input
              class="form-control me-2"
              type="search"
              placeholder="Search"
              aria-label="Search"
            />
            <button class="btn btn-outline-success" type="submit">
              Search
            </button>
          </form>
        </div>
      </nav>
    </div>
  </header>
</template>

<style lang="scss" scoped></style>
