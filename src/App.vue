<template>
  <div id="app">
    <HeaderComponent @performSearch="startSearch"/>

    <main>
      <MainList :moviesList="moviesArray"/>
      <MainList :moviesList="tvSeries" />
    </main>
  </div>
</template>

<script>
import HeaderComponent from './components/HeaderComponent.vue';
import MainList from './components/MainList.vue';

import axios from 'axios';

export default {
  name: 'App',
  components: {
   HeaderComponent,
   MainList
  },
  data() {
    return {
      searchText: '',
      moviesArray: [],
      tvSeries: [],
      url: 'https://api.themoviedb.org/3/search/movie?api_key=859e5e282c5287690662bd43296fa841&query=',
      urlTvSeries: 'https://api.themoviedb.org/3/search/tv?api_key=859e5e282c5287690662bd43296fa841&query='
    }
  },
  methods: {
    startSearch(textToSearch) {
      this.searchText = textToSearch;

      if(this.searchText !== '') {
        this.getMovies();
        this.getTvSeries();
      }
    },
    getMovies() {
      let textMovie = this.searchText.replaceAll(' ', '+');

      let url = this.url + textMovie;

      axios.get(url)
      .then((results) => {
        this.moviesArray = results.data.results;
      })

      .catch((err) => {
        console.log('Error', err);
      });
    },
    getTvSeries() {
      let textTvSeries = this.searchText.replaceAll(' ', '+');

      let urlTv = this.urlTvSeries + textTvSeries;

      axios.get(urlTv)
      .then((result) => {
        this.tvSeries = result.data.results;
      });
    }
  }
}
</script>

<style lang="scss">
@import './style/common.scss'
</style>
