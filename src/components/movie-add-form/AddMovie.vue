<template>
  <div id="addMovieForm" class="section">
    <div class="container">
      <h2 class="sub-heading">Add Movie</h2>
      <div class="form-container">
        <div class="preview">
          <h3>Preview</h3>
          <omdb-movie-card :title="title" :poster="poster" />
        </div>
        <add-movie-form @titleChange="title = $event" @posterChange="poster = $event" :title="title" :poster="poster" />
      </div>
    </div>
  </div>
</template>

<script>
import MovieCard from '../movie-listing/MovieCard.vue'
import AddMovieForm from './AddMovieForm.vue'

export default {
  data() {
    return {
      title: '',
      poster: ''
    }
  },
  name: 'AddMovie',
  components: {
    'omdb-movie-card': MovieCard,
    'add-movie-form': AddMovieForm
  }
}
</script>

<style>
#addMovieForm {
  background-color: rgb(11, 29, 46);
}
#addMovieForm .form-container {
  display: flex;
  flex-direction: row;
}

.sub-heading {
  font-size: 2rem;
  color: #ffffff;
  margin-bottom: 50px;
}

.preview h3 {
  text-align: left;
  font-weight: lighter;
}
</style>