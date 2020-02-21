<template>
  <div id="content">
    <omdb-movie-listing />
    <omdb-add-movie />
  </div>
</template>

<script>
import MovieListing from './movie-listing/MovieListing.vue'
import AddMovie from './movie-add-form/AddMovie.vue'

export default {
  name: 'Content',
  components: {
    'omdb-movie-listing': MovieListing,
    'omdb-add-movie': AddMovie
  }
}
</script>

<style>
#content {
  background-color: rgb(15, 38, 61);
}

.container {
  max-width: 1200px;
  margin: 0 auto;
}

/* @media only screen and (max-width: 600px) {
  #content {
    padding: 100px 0;
  }
} */
</style>