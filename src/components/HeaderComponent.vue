<template>
    <header>
        <input v-model="textMovie" @keyup.enter="$emit('performSearch', textMovie)" type="text">
        <button @click="$emit('performSearch', textMovie)">Cliccami</button>
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