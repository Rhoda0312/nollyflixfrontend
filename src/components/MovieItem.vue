<template>
    <div class="movie-item" @click="toggleDetails">
      <div class="thumbnail-container">
        <img :src="movie.image" alt="Movie Thumbnail">
        <div class="movie-details" v-show="showDetails">
          <h3>{{ movie.title }}</h3>
          <p>{{ movie.description }}</p>
          <p>Genre: {{ movie.genre }}</p>
          <p>Rating: {{ movie.pgRating }}</p>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: 'MovieItem',
    props: {
      movie: Object
    },
    data() {
      return {
        showDetails: false
      };
    },
    methods: {
      toggleDetails() {
        this.showDetails = !this.showDetails;
      }
    }
  };
  </script>
  
  <style scoped>
.movie-item {
  border: 1px solid #ddd;
  border-radius: 5px;
  overflow: hidden;
  height: 300px; /* Fixed height */
  cursor: pointer;
  position: relative;
}

.thumbnail-container img {
  width: 100%;
  height: 100%;
  object-fit: cover; /* Maintain aspect ratio */
}

.movie-details {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: rgba(0, 0, 0, 0.7);
  color: white;
  padding: 1rem;
  opacity: 0;
  transition: opacity 0.3s ease;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.movie-item:hover .movie-details,
.movie-item:active .movie-details {
  opacity: 1;
}
</style>
