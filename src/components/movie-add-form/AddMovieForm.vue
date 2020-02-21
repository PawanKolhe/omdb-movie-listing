<template>
  <div id="addMovieForm">
    <div class="input-row">
      <label>Title</label>
      <input @keyup="changeName" type="text" v-model="title" />
    </div>
    <div class="input-row">
      <label>Poster Image URL</label>
      <input @keyup="changePoster" type="text" v-model="poster" />
    </div>
    <div class="input-row">
      <input class="button" @click.prevent="" type="submit" value="Add Movie" />
    </div>
  </div>
</template>

<script>
export default {
  props: ['title', 'poster'],
  methods: {
    changeName(event) {
      this.title = event.target.value;
      this.$emit('titleChange', this.title);
    },
    changePoster(event) {
      this.poster = event.target.value;
      this.$emit('posterChange', this.poster);
    }
  }
}
</script>

<style>
#addMovieForm {
  display: flex;
  flex-direction: column;
  flex: auto;
  padding: 30px;
  position: relative;
}
#addMovieForm .movie {
  width: 280px;
}

.input-row {
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  margin-bottom: 30px;
}
.input-row:last-child {
  margin-bottom: 0px;
}
.input-row label {
  font-size: 1.2rem;
  text-align: left;
  color: #ffffff;
  margin-bottom: 5px;
}
.input-row input[type="text"] {
  font-size: 1.5rem;
  border-radius: 5px;
  padding: 10px 15px;
  outline: none;
  border: 5px solid rgb(26, 65, 104);
}

.button {
  font-size: 1.2rem;
  padding: 15px;
  color: #ffffff;
  background-color: #1A4168;
  outline: none;
  border: none;
  border-radius: 5px;
  border-bottom: 5px solid rgb(17, 45, 73);
}
.button:active {
  transform: translateY(2px);
}
</style>