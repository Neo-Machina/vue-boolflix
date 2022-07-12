<template>
    <header>
        <input v-model="textMovie" type="text">
        <button @click="getMovies()">Cliccami</button>
    </header>
</template>

<script>
import axios from 'axios';

export default {
    name: 'HeaderComponent',
    components: {

    },
    data() {
        return {
            url:'https://api.themoviedb.org/3/search/movie?api_key=859e5e282c5287690662bd43296fa841&query=',
            moviesArray: [],
            textMovie: ''
        }
    },
    methods: {
        getMovies() {
            let textMovie = this.textMovie.replaceAll(' ', '+');

            this.url = this.url + textMovie;
            
            axios.get(this.url)
            .then((results) => {
                this.moviesArray = results.data.results;
            })
            .catch((err) => {
                console.log('Error', err);
            });
        },



    }
}
</script>

<style scoped lang="scss">
header{
    height: 100px;
    background-color: lightblue;
}
</style>