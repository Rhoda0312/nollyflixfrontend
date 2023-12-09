<template>
  <div id="app">
    <Navbar />
    <MovieGrid />
    <Footer />
  </div>
</template>

<script>
import Navbar from './components/Navbar.vue';
import MovieGrid from './components/MovieGrid.vue';
import Footer from './components/Footer.vue';

export default {
  name: 'App',
  components: {
    Navbar,
    MovieGrid,
    Footer
  }
};
</script>

<style>
#app {
  min-height: 100vh;
  position: relative;
  padding-bottom: 60px; 
}
</style>
