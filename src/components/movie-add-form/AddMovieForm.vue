<template>
  <form class="add-movie-form">
    <div class="input-row">
      <label for='title'>Title</label>
      <input class="input-field" @keyup="changeName" type="text" name="title" v-model="inputTitle" />
    </div>
    <div class="input-row">
      <label for="poster">Poster Image URL</label>
      <input class="input-field" @keyup="changePoster" type="url" name="poster" v-model="inputPoster" />
    </div>
    <div v-if="errors.length" class="error-text">
      <div v-for="error in errors" :key="error">{{ error }}</div>
    </div>
    <div class="input-row">
      <input class="button" @click.prevent="checkForm" type="submit" value="Add Movie" />
    </div>
  </form>
</template>

<script>
export default {
  data() {
    return {
      inputTitle: '',
      inputPoster: '',
      errors: []
    }
  },
  props: ['title', 'poster'],
  methods: {
    changeName(event) {
      this.inputTitle = event.target.value;
      this.$emit('titleChange', this.inputTitle);
    },
    changePoster(event) {
      this.inputPoster = event.target.value;
      this.$emit('posterChange', this.inputPoster);
    },
    addMovie() {
      this.$emit('addMovie', { Title: this.inputTitle, Poster: this.inputPoster});
    },
    checkForm() {
      function is_url(str) {
        let regexp =  /^(?:(?:https?|ftp):\/\/)?(?:(?!(?:10|127)(?:\.\d{1,3}){3})(?!(?:169\.254|192\.168)(?:\.\d{1,3}){2})(?!172\.(?:1[6-9]|2\d|3[0-1])(?:\.\d{1,3}){2})(?:[1-9]\d?|1\d\d|2[01]\d|22[0-3])(?:\.(?:1?\d{1,2}|2[0-4]\d|25[0-5])){2}(?:\.(?:[1-9]\d?|1\d\d|2[0-4]\d|25[0-4]))|(?:(?:[a-z\u00a1-\uffff0-9]-*)*[a-z\u00a1-\uffff0-9]+)(?:\.(?:[a-z\u00a1-\uffff0-9]-*)*[a-z\u00a1-\uffff0-9]+)*(?:\.(?:[a-z\u00a1-\uffff]{2,})))(?::\d{2,5})?(?:\/\S*)?$/;
        if (regexp.test(str)) {
          return true;
        }
        else {
          return false;
        }
      }

      // form validation
      if(this.inputTitle && this.inputPoster && is_url(this.inputPoster)) {
        this.addMovie();
      }

      this.errors = [];
      if (!this.inputTitle) {
        this.errors.push('Title required.');
      }
      if (!this.inputPoster) {
        this.errors.push('Poster URL required.');
      } else if(!is_url(this.inputPoster)) {
        this.errors.push('Poster URL invalid.');
      }
    }
  },
  watch: {
    title(newVal) {
      this.inputTitle = newVal;
    },
    poster(newVal) {
      this.inputPoster = newVal;
    }
  }
}
</script>

<style>
.add-movie-form {
  display: flex;
  flex-direction: column;
  flex: auto;
  padding: 30px;
  position: relative;
  align-items: center;
  justify-content: center;
}
.add-movie-form .movie {
  width: 280px;
}

.input-row {
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  margin-bottom: 30px;
  width: 100%;
}
.input-row:last-child {
  margin-bottom: 0px;
}
.input-row label {
  font-size: 1.2rem;
  text-align: left;
  color: #ffffff;
  margin-bottom: 5px;
  font-family: var(--font-family-2);
}
.input-field {
  font-size: 1.5rem;
  border-radius: 5px;
  padding: 10px 15px;
  outline: none;
  border: 5px solid rgb(26, 65, 104);
}
.input-field:focus {
  border: 5px solid rgb(41, 100, 158);
}

.button {
  font-size: 1.2rem;
  width: 100%;
  padding: 15px;
  color: #ffffff;
  background-color: rgb(26, 65, 104);
  outline: none;
  border: none;
  border-radius: 5px;
  border-bottom: 5px solid rgb(17, 45, 73);
  cursor: pointer;
}
.button:hover {
  background-color: rgb(30, 77, 124);
}
.button:active {
  transform: translateY(2px);
}

.error-text {
  width: 100%;
  text-align: left;
  color: #d32f2f;
  font-weight: lighter;
  margin-bottom: 25px;
}

@media only screen and (max-width: 800px) {
  .add-movie-form {
    width: 100%;
    padding: 5px;
  }
}
</style>