<template>
  <div class="movie">
    <div @click="openModal" class="movie-poster">
      <img :src="poster ? poster : ''">
      <div class="overlay" :class="{ overlayDisable: modalDisable }">
        <button>More Details</button>
      </div>
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
    },
    modalDisable: {
      type: Boolean,
      default: false
    }
  },
  methods: {
    openModal() {
      if(!this.modalDisable) {
        this.modalVisible = !this.modalVisible;
      }
    }
  },
  mounted() {
    axios
      .get(`https://www.omdbapi.com/?i=${this.imdbID}&apikey=e0620bd4`)
      .then(response => (this.movieDetail = response.data));
  }
}
</script>

<style>
.movie {
  overflow: hidden;
}

.overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.6);
  z-index: 10;
  display: none;
  align-items: center;
  justify-content: center;
}
.overlay button {
  font-size: 1.1rem;
  border-radius: 5px;
  font-weight: bold;
  background-color: #8BC34A;
  color: #ffffff;
  padding: 12px;
  border: none;
  outline: none;
  cursor: pointer;
}
.overlayDisable {
  display: none;
}
.overlayDisable button {
  display: none;
}

.movie:hover .overlay {
  display: flex;
}

.movie-poster {
  width: 100%;
  margin-bottom: 5px;
  border: 5px solid #fff;
  border-radius: 5px;
  cursor: pointer;
  position: relative;
}
.movie:hover .movie-poster {
  border: 5px solid #8BC34A;
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
.movie-title:hover {
  color: rgba(255, 255, 255, 0.75);
}
.movie-year {
  color: rgb(99, 131, 163);
  font-size: 1.1rem;
  margin-top: 5px;
}

@media (max-width: 700px) {
  
}
</style>