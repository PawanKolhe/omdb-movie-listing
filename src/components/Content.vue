<template>
  <div id="content">
    <div class="container">
      <omdb-movie-listing />
    </div>
  </div>
</template>

<script>
import MovieListing from './MovieListing'

export default {
  name: 'Content',
  components: {
    'omdb-movie-listing': MovieListing
  }
}
</script>

<style>
#content {
  padding: 60px 0;
  background-color: rgb(15, 38, 61);
}

.container {
  max-width: 1200px;
  margin: 0 auto;
}
.container .row:first-child {
  margin-top: 0px;
}
.container .row:last-child {
  margin-bottom: 0px;
}

@media only screen and (max-width: 600px) {
  #content {
    padding: 100px 0;
  }
}
</style>