<template>
  <div id="addMovieForm" class="section">
    <div class="container">
      <h2 class="sub-heading"><span class="iconify" data-icon="mdi:video-plus-outline" data-inline="false"></span>Add Movie</h2>
      <div class="form-container">
        <div class="preview">
          <h3>Preview</h3>
          <omdb-movie-card :title="title" :poster="poster" :modalDisable="true" />
        </div>
        <add-movie-form @titleChange="title = $event" @posterChange="poster = $event" @addMovie="addMovieToListing" :title="title" :poster="poster" />
      </div>
    </div>
  </div>
</template>

<script>
import MovieCard from '../movie-listing/MovieCard.vue'
import AddMovieForm from './AddMovieForm.vue'

// import DefaultImage from '../../assets/default-movie.png'

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
  }
}
</script>

<style>
#addMovieForm {
  background-color: rgb(11, 29, 46);
  display: flex;
  flex-direction: column;
  flex: auto;
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
  display: flex;
  justify-content: center;
  align-items: center;
}
.sub-heading .iconify {
  margin-right: 10px;
  font-size: 3.5rem;
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