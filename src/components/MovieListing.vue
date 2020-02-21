<template>
  <div class="movie-listing">
    <omdb-movie v-for="(movie, index) in getMovies" :key="index" :title="movie.Title" :poster="movie.Poster" :year="movie.Year" :imdbID="movie.imdbID" />
  </div>
</template>

<script>
import Movie from './Movie.vue'

import axios from 'axios';

export default {
  data() {
    return {
      movies: []
    }
  },
  name: 'MovieListing',
  components: {
    'omdb-movie': Movie
  },
  computed: {
    getMovies() {
      return this.movies.filter(movie => movie.Type == 'movie');
    }
  },
  mounted() {
    axios
      .get('http://www.omdbapi.com/?s=harry%20potter&apikey=e0620bd4')
      .then(response => (this.movies = response.data.Search));
  }
}
</script>

<style>
.movie-listing {
  padding: 40px;
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(180px, 1fr));
  justify-content: center;
  align-items: stretch;
  grid-gap: 35px 6%;
}
</style>