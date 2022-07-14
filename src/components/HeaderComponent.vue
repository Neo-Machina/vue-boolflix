<template>
    <header>
        <h2>boolflix</h2>

        <div class="search_bar">
            <input class="search_item" v-model="textMovie" 
                    @keyup.enter="$emit('performSearch', textMovie)"    
                    type="text" placeholder="Write in the Movie's or TvSeries' name">
            <button class="search_item" @click="$emit('performSearch', textMovie)">Search</button>
        </div>
    </header>
</template>

<script>

export default {
    name: 'HeaderComponent',
    props: {
        moviesArray: Array
    },
    data() {
        return {
            textMovie: ''
        }
    }
}
</script>

<style scoped lang="scss">
@import '../style/variables.scss';

header{
    height: 90px;
    background-color: black;
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 0 25px;
    
    h2 {
        color: red;
        text-transform: $uppercase_text;
        font-size: 35px;
    }

    .search_bar {
        .search_item {
            padding: 4px 10px;
            font-size: 16px;
            border-radius: 10px;
        }

        input {
            width: 300px;
        }

        button {
            margin-left: 20px;
        }
    }
}
</style>