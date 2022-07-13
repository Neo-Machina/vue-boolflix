<template>
    <div class="container">
        <div class="row">
            <div class="col" 
            v-for="albumItem in moviesArray"
            :key="albumItem.id"  
            :album="albumItem">
                <MovieCard />
            </div>
        </div>
    </div>
</template>

<script>
import MovieCard from './MovieCard.vue';
import axios from 'axios';

export default {
    name: 'MoviesList',
    components: {
        MovieCard
    },
    props: {
        singleAlbum: String
    },
    data() {
        return {
            url:'https://api.themoviedb.org/3/search/movie?api_key=859e5e282c5287690662bd43296fa841&query=',
            moviesArray: [],
            searchText: ''
        }
    },
    created() {
        this.getMovies;
    },
    methods: {
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

                this.$emit('moviesReady', this.moviesArray)
            })

            .catch((err) => {
                console.log('Error', err);
            });
            },
            searchMovie(word) {
            this.serchText = word;
        }
    }
}
</script>

<style lang="sass" scoped>

</style>