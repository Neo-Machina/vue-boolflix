<template>
    <div class="container">
        <div class="row">
            <div class="col" 
            v-for="albumItem in moviesList"
            :key="albumItem.id">
                <MovieCard :album="albumItem" />
            </div>
        </div>
    </div>
</template>

<script>
import MovieCard from './MovieCard.vue';


export default {
    name: 'MoviesList',
    components: {
        MovieCard
    },
    props: {
        moviesList: Array
    },
    data() {
        return {
            
        }
    },
    created() {
       
    },
    methods: {
        
        
    }
}
</script>

<style lang="scss" scoped>

</style>