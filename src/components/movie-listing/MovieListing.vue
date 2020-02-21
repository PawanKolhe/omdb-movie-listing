<template>
  <div class="movie-listing section">
    <div class="container">
      <omdb-movie-card v-for="(movie, index) in getMovies" :key="index" :title="movie.Title" :poster="movie.Poster" :year="movie.Year" :imdbID="movie.imdbID" />
    </div>
  </div>
</template>

<script>
import MovieCard from './MovieCard.vue'

export default {
  props: ['newMovies'],
  name: 'MovieListing',
  components: {
    'omdb-movie-card': MovieCard
  },
  computed: {
    getMovies() {
      return this.newMovies;
    }
  }
}
</script>

<style>
.movie-listing .container {
  padding: 0px 40px;
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(180px, 1fr));
  justify-content: center;
  align-items: stretch;
  grid-gap: 35px 6%;
}
</style>