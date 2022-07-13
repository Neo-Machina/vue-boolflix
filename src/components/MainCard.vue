<template>
    <div class="singleItem_content">
        <div>{{ singleItem.title ? singleItem.title : singleItem.name }}</div>

        <div>{{ singleItem.original_title ? singleItem.original_title : singleItem.original_name }}</div>

        <img class="flag_language"
            v-if="languageArray.includes(singleItem.original_language)" 
            :src="getFlagImg" :alt="singleItem.original_language">

        <div v-else>{{ singleItem.original_language }}</div>

        <div>{{ singleItem.vote_average }}</div>

        <img class="poster_item"
            :src="!singleItem.poster_path ? 'https://eiflixnob.live/assets/general/images/no_poster.jpg' : imageItem" 
            :alt="singleItem.title ? singleItem.title : singleItem.name">
        
        <div class="star_icon">
            <font-awesome-icon v-for="(star,index) in 5" :key="index" :icon="getStarsStyle(star)" />
        </div>
        
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
            languageArray: [
                'it',
                'en',
                'fr',
                'ko',
                'ja'
            ]
        }
    },
    computed: {
        imageItem() {
            return this.urlImg + this.singleItem.poster_path;
        },
        getFlagImg() {
            if(this.singleItem.original_language === 'it') {
                return require('../assets/img/italy.png');
            } else if(this.singleItem.original_language === 'en') {
                return require('../assets/img/england.png');
            } else if(this.singleItem.original_language === 'fr') {
                return require('../assets/img/france.png');
            } else if(this.singleItem.original_language === 'ja') {
                return require('../assets/img/japan.png');
            } else {
                return require('../assets/img/korea.png');
            }         
        }
    },
    methods: {
        transformVote() {
            return Math.ceil((this.singleItem.vote_average * 5) / 10);
        },
        getStarsStyle(starNumber) {
            if(starNumber <= this.transformVote()) {
                return 'fa-solid fa-star';
            } else {
                return 'fa-regular fa-star'
            }
        }
    }
}
</script>

<style lang="scss" scoped>
.singleItem_content {
    background-color: lightgreen;
    padding: 10px;
    margin: 10px;

    .flag_language {
        width: 25px;
    }

    .poster_item {
        width: 342px;
    }

    .star_icon {

    }
}
</style>