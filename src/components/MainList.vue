<template>
    <section>
        <div class="row">
            <div class="col" 
                v-for="item in moviesList"
                :key="item.id">
                <MainCard :singleItem="item" />
            </div>
        </div>
    </section>
</template>

<script>
import MainCard from './MainCard.vue';


export default {
    name: 'MainList',
    components: {
        MainCard
    },
    props: {
        moviesList: Array,
    }
}
</script>

<style lang="scss" scoped>
.row {
    display: flex;
    flex-wrap: wrap;
    margin-left: 20px;
    padding-bottom: 20px;

    .col {
        margin: 20px 25px 0 0;
    }
}
</style>