<template>
  <div class="movie">
    <div class="movie-poster">
      <img @click="openModal" :src="poster">
    </div>
    <div class="movie-text">
      <div @click="openModal" class="movie-title">{{ title }}</div>
      <div class="movie-year">{{ year }}</div>
      <modal :modalVisible="modalVisible" :title="title" :poster="poster" :movieDetail="movieDetail" @closeModal="modalVisible = $event" />
    </div>
  </div>
</template>

<script>
import Modal from './Modal.vue';

import axios from 'axios';

export default {
  data() {
    return {
      movieDetail: {},
      modalVisible: false
    }
  },
  components: {
    'modal': Modal
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
  methods: {
    openModal() {
      console.log(this);
      this.modalVisible = !this.modalVisible;
    }
  },
  mounted() {
    axios
      .get(`http://www.omdbapi.com/?i=${this.imdbID}&apikey=e0620bd4`)
      .then(response => (this.movieDetail = response.data));
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
  font-family: var(--font-family-1);
  cursor: pointer;
  word-break: break-word;
}
.movie-year {
  color: rgb(99, 131, 163);
  font-size: 1.1rem;
  margin-top: 5px;
}
</style>