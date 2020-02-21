<template>
  <div class="movie">
    <div class="movie-poster">
      <img :src="poster">
    </div>
    <div class="movie-text">
      <div class="movie-title">{{ title }}</div>
      <div class="movie-year">{{ year }}</div>
    </div>
  </div>
</template>

<script>
// import axios from 'axios';

export default {
  data() {
    return {
      movieDetail: {}
    }
  },
  name: 'MovieCard',
  props: {
    title: {
      type: String,
      required: true
    },
    poster: {
      type: String,
      required: true
    },
    year: {
      type: String
    },
    imdbID: {
      type: String
    }
  },
  mounted() {
    // axios
    //   .get(`http://www.omdbapi.com/?i=${this.imdbID}&apikey=e0620bd4`)
    //   .then(response => (this.movieDetail = response.data));
  }
}
</script>

<style>
.movie {
  overflow: hidden;
}

.movie-poster {
  width: 100%;
  margin-bottom: 5px;
  border: 5px solid #fff;
  border-radius: 5px;
  cursor: pointer;
  /* min-width: 200px; */
}
.movie-poster img {
  width: 100%;
  height: auto;
}
.movie-text {
  padding: 5px 0;
  text-align: left;
  
}
.movie-title {
  font-size: 1.3rem;
  color: #fff;
  font-weight: bold;
  font-family: 'Roboto Condensed', sans-serif;
  cursor: pointer;
}
.movie-year {
  color: rgb(99, 131, 163);
  font-size: 1.1rem;
  margin-top: 5px;
}
</style>