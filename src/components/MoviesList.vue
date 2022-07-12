<template>
    <div class="container">
        <div class="row">
            <div class="col">
                <MovieCard />
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
    data() {
        return {

        }
    }
}
</script>

<style lang="sass" scoped>

</style>