<template>
  <div class="modal-container" v-if="modalVisible">
    <div class="modal">
      <div @click="closeModal" class="modal-close"><span class="iconify" data-icon="fa-solid:times" data-inline="false"></span></div>

      <div>
        <div class="modal-title">{{ title }} <span class="light">({{ movieDetail.Year }})</span></div>
        <div v-if="movieDetail.imdbRating" class="imdbRating"><span class="imdb">IMDb</span>{{ movieDetail.imdbRating }}</div>
        <div v-if="movieDetail.Plot" class="modal-sub-container">
          <div class="modal-sub-title">Plot</div>
          <div>{{ movieDetail.Plot }}</div>
        </div>
        <div class="modal-box">
          <div class="modal-col gs-modal-col-3">
            <div v-if="movieDetail.Director" class="modal-sub-container">
              <div class="modal-sub-title">Director</div>
              <div>{{ movieDetail.Director }}</div>
            </div>
            <div v-if="movieDetail.Writer" class="modal-sub-container">
              <div class="modal-sub-title">Writers</div>
              <div>{{ movieDetail.Writer }}</div>
            </div>
            <div v-if="movieDetail.Actors" class="modal-sub-container">
              <div class="modal-sub-title">Actors</div>
              <div>{{ movieDetail.Actors }}</div>
            </div>
            <div v-if="movieDetail.Production" class="modal-sub-container">
              <div class="modal-sub-title">Production</div>
              <div>{{ movieDetail.Production }}</div>
            </div>
          </div>
          <div class="modal-col gs-modal-col-1">
            <div v-if="movieDetail.Language" class="modal-sub-container">
              <div class="modal-sub-title">Language</div>
              <div>{{ movieDetail.Language }}</div>
            </div>
            <div v-if="movieDetail.Runtime" class="modal-sub-container">
              <div class="modal-sub-title">Runtime</div>
              <div>{{ movieDetail.Runtime }}</div>
            </div>
            <div v-if="movieDetail.Ratings" class="modal-sub-container">
              <a target="_blank">
                <div class="modal-sub-title">Rating</div>
                <div v-for="(rating, index) in movieDetail.Ratings" :key="index">{{ rating.Source }} - {{ rating.Value }}</div>
              </a>
            </div>
          </div>
        </div>
      </div>
      
    </div>
  </div>
</template>

<script>


export default {
  name: 'Modal',
  props: ['modalVisible', 'movieDetail', 'title', 'poster'],
  methods: {
    closeModal() {
      this.$emit('closeModal', false);
    }
  }
}
</script>

<style scoped>
.light {
  font-weight: lighter;
}

.modal-container {
  position: fixed;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  z-index: 999;
  padding: 5%;
  justify-content: center;
  align-items: center;
  overflow: auto;
  display: flex;
}

.modal {
  background-color: #ffffff;
  border-radius: 10px;
  width: 100%;
  max-width: 800px;
  height: 80%;
  position: relative;
  padding: 30px;
  overflow-y: auto;
  overflow-x: hidden;
  font-family: var(--font-family-2);
  color: #212121;
  z-index: 1100;
}

.modal-close {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 40px;
  height: 40px;
  border-radius: 10px;
  position: absolute;
  top: 15px;
  right: 15px;
  color: #ffffff;
  background-color: rgb(64, 156, 243);
  box-shadow: 0px 0px 15px #3e88ff;
  overflow: hidden;
  cursor: pointer;
}
.modal-close:hover {
  background-color: rgba(64, 156, 243, 0.85);
}

.modal-title {
  color: rgb(40, 96, 148);
  font-family: var(--font-family-2);
  font-size: 1.9rem;
  font-weight: bold;
  margin-bottom: 0px;
  padding-right: 30px;
}

.modal-sub-title {
  font-size: 1.5rem;
  color: rgb(54, 118, 179);
  margin-top: 20px;
  margin-bottom: 5px;
}

.modal-box {
  display: flex;
  flex-direction: row;
}

.modal-col:not(:last-child) {
  padding-right: 30px;
}
.modal-col-1 {
  flex: 1;
}
.modal-col-2 {
  flex: 2;
}
.modal-col-3 {
  flex: 3;
}
.modal-col-4 {
  flex: 4;
}
.modal-col-5 {
  flex: 5;
}
.modal-col-auto {
  flex: auto;
}

.gs-modal-backicon-1 {
  position: absolute;
  bottom: 25px;
  right: -25px;
  opacity: 0.05;
  transform: rotate(-45deg);
}
.gs-modal-backicon-1 img {
  width: 100px;
}

.imdbRating {
  margin-top: 8px;
  background: #F5C518;
  color: #212121;
  font-weight: bold;
  font-size: 1.3rem;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  padding: 3px 8px;
  border-radius: 5px;
  font-family: var(--font-family-2);
}
.imdbRating .imdb {
  font-family: Impact, Haettenschweiler, 'Arial Narrow Bold', sans-serif;
  font-weight: lighter;
  margin-right: 5px;
}


@media (max-width: 700px) {
  .modal-title {
    font-size: 1.6rem;
  } 
  .modal-box {
    flex-direction: column;
  }
  .modal-sub-title {
    font-size: 1.3rem;
  }
  .modal {
    padding: 30px 20px;
  }
}
@media (max-width: 500px) {
  .modal-close {
    background-color: #ffffff;
    color: rgb(64, 156, 243);
    border: 1px solid rgb(64, 156, 243);
    box-shadow: none;
  }
  .modal-close:hover {
    background-color: #ffffff;
  }
}
@media (max-width: 400px) {
  .modal-title {
    font-size: 1.5rem;
  }
}
</style>