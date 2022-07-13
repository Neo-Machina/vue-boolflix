<template>
    <div class="album_content">
        <div>{{ album.title }}</div>
        <div>{{ album.original_title }}</div>
        <div>{{ album.original_language }}</div>
        <div>{{ album.vote_average }}</div>
    </div>
</template>

<script>
export default {
    name: 'MovieCard',
    props: {
        album: Object
    },
    data() {
        return {

        }
    }
}
</script>

<style lang="scss" scoped>
.album_content {
    background-color: lightgreen;
    padding: 10px;
    margin: 10px;
}
</style>