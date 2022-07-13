<template>
    <div class="singleItem_content">
        <div>{{ singleItem.title ? singleItem.title : singleItem.name }}</div>
        <div>{{ singleItem.original_title ? singleItem.original_title : singleItem.original_name }}</div>
        <div>{{ singleItem.original_language }}</div>
        <div>{{ singleItem.vote_average }}</div>
        <img :src="!singleItem.poster_path ? 'https://eiflixnob.live/assets/general/images/no_poster.jpg' : imageItem" 
            :alt="singleItem.title ? singleItem.title : singleItem.name">
    </div>
</template>

<script>

export default {
    name: 'MainCard',
    props: {
        singleItem: Object
    },
    data() {
        return {
            urlImg: 'https://image.tmdb.org/t/p/w342',
        }
    },
    computed: {
        imageItem() {
            return this.urlImg + this.singleItem.poster_path;
        }
    }
}
</script>

<style lang="scss" scoped>
.singleItem_content {
    background-color: lightgreen;
    padding: 10px;
    margin: 10px;

    img {
        width: 342px;
    }
}
</style>