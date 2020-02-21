<template>
  <div class="movie-listing section">
    <div class="container">
      <omdb-movie-card v-for="(movie, index) in getMovies" :key="index" :title="movie.Title" :poster="movie.Poster" :year="movie.Year" :imdbID="movie.imdbID" />
      <img class="backimage1" src="../../assets/icons/film.svg">
      <img class="backimage2" src="../../assets/icons/clapperboard.svg">
      <img class="backimage3" src="../../assets/icons/cinema.svg">
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
  position: relative;
}

.backimage1 {
  position: absolute;
  top: 100px;
  left: -250px;
  opacity: 0.03;
  width: 200px;
  height: auto;
}
.backimage2 {
  position: absolute;
  top: 500px;
  right: -250px;
  opacity: 0.03;
  width: 200px;
  height: auto;
}
.backimage3 {
  position: absolute;
  top: 1000px;
  left: -250px;
  opacity: 0.03;
  width: 200px;
  height: auto;
}
</style>