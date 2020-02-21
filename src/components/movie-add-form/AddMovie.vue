<template>
  <div id="addMovieForm" class="section">
    <div class="container">
      <h2 class="sub-heading">Add Movie</h2>
      <div class="form-container">
        <div class="preview">
          <h3>Preview</h3>
          <omdb-movie-card :title="title" :poster="getPoster" :modalDisable="true" />
        </div>
        <add-movie-form @titleChange="title = $event" @posterChange="poster = $event" @addMovie="addMovieToListing" :title="title" :poster="poster" />
      </div>
    </div>
  </div>
</template>

<script>
import MovieCard from '../movie-listing/MovieCard.vue'
import AddMovieForm from './AddMovieForm.vue'

import DefaultImage from '../../assets/default-movie.png'

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
  },
  methods: {
    addMovieToListing(value) {
      this.$emit('addMovieToListing', value);
    }
  },
  computed: {
    getPoster() {
      return (this.poster ? this.poster : DefaultImage);
    }
  }
}
</script>

<style>
#addMovieForm {
  background-color: rgb(11, 29, 46);
  display: flex;
  flex-direction: column;
  flex: auto;
  padding: 30px;
  position: relative;
}
#addMovieForm .form-container {
  display: flex;
  flex-direction: row;
  justify-content: stretch;
  max-width: 700px;
}

.sub-heading {
  font-size: 2.5rem;
  color: #ffffff;
  margin-bottom: 30px;
  font-family: var(--font-family-2);
}

.preview h3 {
  text-align: left;
  font-weight: lighter;
  color: rgb(69, 123, 177);
}

.preview .movie {
  max-width: 300px;
}

@media only screen and (max-width: 800px) {
  #addMovieForm .form-container {
    display: flex;
    flex-direction: column-reverse;
    justify-content: center;
    align-items: center;
  }
  .preview h3 {
    text-align: center;
  }

  #addMovieForm {
    width: 100%;
  }
  #addMovieForm .movie {
    width: 100%;
  }
}
</style>