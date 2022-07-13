<template>
  <div id="app">
    <HeaderComponent @performSearch="startSearch"/>

    <main>
      <MoviesList :moviesList="moviesArray"/>
    </main>
  </div>
</template>

<script>
import HeaderComponent from './components/HeaderComponent.vue';
import MoviesList from './components/MoviesList.vue';

import axios from 'axios';

export default {
  name: 'App',
  components: {
   HeaderComponent,
   MoviesList
  },
  data() {
    return {
      searchText: '',
      moviesArray: [],
      url:'https://api.themoviedb.org/3/search/movie?api_key=859e5e282c5287690662bd43296fa841&query='
    }
  },
  methods: {
    // getAlbumArray(allMovies) {
    //   this.moviesList = allMovies;
    // },  
    startSearch(textToSearch) {
      this.searchText = textToSearch;
      if(this.searchText !== '') {
        this.getMovies();
      }
    },
    getMovies() {
      let textMovie = this.searchText.replaceAll(' ', '+');

      let url = this.url + textMovie;

      axios.get(url)
      .then((results) => {
        this.moviesArray = results.data.results;

        this.moviesArray.forEach((movie) => {
            if(!this.moviesArray.includes(movie)) {
                this.moviesArray.push(movie);
            }
        });
      })

      .catch((err) => {
        console.log('Error', err);
      });
    },
  }
}
</script>

<style lang="scss">
@import './style/common.scss'
</style>
