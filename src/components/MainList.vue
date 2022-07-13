<template>
    <div class="container">
        <div class="row">
            <div class="col" 
            v-for="item in moviesList"
            :key="item.id">
                <MainCard :singleItem="item" />
            </div>
        </div>
    </div>
</template>

<script>
import MainCard from './MainCard.vue';


export default {
    name: 'MainList',
    components: {
        MainCard
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