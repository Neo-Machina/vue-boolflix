<template>
    <div class="singleItem_content">
        <div class="info_card" :id="singleItem.id" @mouseleave="onMouseLeave()">
            <div>
                <span class="bold_text">Title</span>:
                {{ singleItem.title ? singleItem.title : singleItem.name }}
            </div>

            <div>
                <span class="bold_text">Original title</span>: 
                {{ singleItem.original_title ? singleItem.original_title : singleItem.original_name }}
            </div>

            <img class="flag_language"
                v-if="languageArray.includes(singleItem.original_language)" 
                :src="getFlagImg" :alt="singleItem.original_language">

            <div v-else>{{ singleItem.original_language }}</div>

            <div class="average_vote"> 
                <span class="bold_text">Vote</span>: 
                <span class="star_icon">
                    <font-awesome-icon v-for="(star,index) in 5" :key="index" :icon="getStarsStyle(star)" />
                </span>
            </div>

            <div>
                <span class="bold_text">Overview</span>: 
                {{ singleItem.overview }}
            </div>
        </div>

        <img @mouseenter="onMouseEnter()" 
            class="poster_item" :id="'image_' + singleItem.id"
            :src="!singleItem.poster_path ? 'https://eiflixnob.live/assets/general/images/no_poster.jpg' : imageItem" 
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
            return Math.round((this.singleItem.vote_average * 5) / 10);
        },
        getStarsStyle(starNumber) {
            if(starNumber <= this.transformVote()) {
                return 'fa-solid fa-star';
            } else {
                return 'fa-regular fa-star'
            }
        },
        onMouseEnter() {
            document.getElementById(this.singleItem.id).style.display = "unset";
            document.getElementById('image_' + this.singleItem.id).style.filter = "brightness(0.2)";
        },
        onMouseLeave() {    
            document.getElementById(this.singleItem.id).style.display = null;
            document.getElementById('image_' + this.singleItem.id).style.filter = null;

        }
        
    }
}
</script>

<style lang="scss" scoped>
.singleItem_content {
    border: 2px solid white;
    color: white;
    position: relative;

    .info_card {
        display: none;
        position: absolute;
        padding: 60px 20px;
        overflow-y: overlay;
        height: 100%;  
        z-index: 10; 

        .bold_text {
            font-weight: bold;
        }

        .flag_language {
            width: 25px;
        }

        .average_vote { 
            .star_icon {
                color: gold;
            }
        }   
    }

    .poster_item {
        width: 342px;
        height: 513px;
        object-fit: cover;
    }
}
</style>