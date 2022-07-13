<template>
  <div id="app">
    <HeaderComponent :moviesArray="moviesList" @performSearch="startSearch"/>

    <main>
      <MoviesList :singleAlbum="albumToSearch" @moviesReady="getAlbumArray"/>
    </main>
  </div>
</template>

<script>
import HeaderComponent from './components/HeaderComponent.vue';
import MoviesList from './components/MoviesList.vue';



export default {
  name: 'App',
  components: {
   HeaderComponent,
   MoviesList
  },
  data() {
    return {
      albumToSearch: '',
      moviesList: []
    }
  },
  methods: {
    getAlbumArray(allMovies) {
      this.moviesList = allMovies;
    },  
    startSearch(textToSearch) {
      this.albumToSearch = textToSearch;
    }
  }
}
</script>

<style lang="scss">
@import './style/common.scss'
</style>
