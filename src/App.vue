<template>
  <div id="app">
    <HeaderComponent />

    <main>
      <MoviesList />
    </main>
  </div>
</template>

<script>
import HeaderComponent from './components/HeaderComponent.vue';
import MoviesList from './components/MoviesList.vue';


export default {
  name: 'App',
  components: {
   HeaderComponent,
   MoviesList
  }
}
</script>

<style lang="scss">
@import './style/common.scss'
</style>
