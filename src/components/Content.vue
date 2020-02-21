<template>
  <div id="content">
    <omdb-movie-listing :newMovies="movies" />
    <omdb-add-movie @addMovieToListing="addMovieToListing" />
  </div>
</template>

<script>
import MovieListing from './movie-listing/MovieListing.vue'
import AddMovie from './movie-add-form/AddMovie.vue'

import axios from 'axios'

export default {
  data() {
    return {
      movies: []
    }
  },
  name: 'Content',
  components: {
    'omdb-movie-listing': MovieListing,
    'omdb-add-movie': AddMovie
  },
  methods: {
    addMovieToListing(value) {
      this.movies.push(value);
      console.log(this.movies);
    }
  },
  mounted() {
    // fetch movies data
    axios
      .get('http://www.omdbapi.com/?s=harry%20potter&apikey=e0620bd4')
      .then(response => {
        // filter out items that are not movies
        this.movies = response.data.Search.filter(movie => movie.Type == 'movie');
      });
  }
}
</script>

<style>
#content {
  background-color: rgb(15, 38, 61);
}

.section {
  padding: 100px 0;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
}

@media only screen and (max-width: 800px) {
  .container {
    width: 100%;
  }
}
</style>