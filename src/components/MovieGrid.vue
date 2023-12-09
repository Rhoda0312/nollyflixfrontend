<template>
    <div class="movie-grid">
      <!-- Loop over movies array -->
      <MovieItem v-for="movie in movies" :key="movie._id" :movie="movie" />
    </div>
  </template>
  
  <script>
  import MovieItem from './MovieItem.vue';
  
  export default {
    name: 'MovieGrid',
    components: {
      MovieItem
    },
    data() {
      return {
        movies: []
      };
    },
    mounted() {
      this.fetchMovies();
    },
    methods: {
      fetchMovies() {
        fetch('https://nollyflix-c16dcc13299b.herokuapp.com/api')
          .then(response => {
            if (!response.ok) {
              throw new Error(`HTTP error! Status: ${response.status}`);
            }
            return response.json();
          })
          .then(data => {
            this.movies = data.map(movie => ({
              ...movie,
              id: movie._id // Assuming _id is the unique identifier
            }));
          })
          .catch(error => {
            console.error('There has been a problem with your fetch operation:', error);
          });
      }
    }
  };
  </script>
<style scoped>
.movie-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr); /* 2 items per row */
  gap: 1rem;
  width: 90%;
  max-width: 1200px;
  margin: 0 auto; /* Center the grid */
  padding-top: 2rem; /* Added top padding */
}

@media (max-width: 768px) {
  .movie-grid {
    grid-template-columns: 1fr; /* 1 item per row on smaller screens */
  }
}
</style>