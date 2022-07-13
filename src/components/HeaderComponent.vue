<template>
    <header>
        <input v-model="textMovie" @keyup.enter="$emit('performSearch', textMovie)" type="text" placeholder="Inserisci nome del film o serie TV">
        <button @click="$emit('performSearch', textMovie)">Click</button>
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
header{
    height: 100px;
    background-color: lightblue;
}
</style>