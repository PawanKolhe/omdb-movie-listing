<template>
  <div id="app">
    <omdb-header />
    <omdb-content />
    <omdb-footer />
  </div>
</template>

<script>
import Header from './components/Header';
import Content from './components/Content';
import Footer from './components/Footer';

export default {
  name: 'App',
  components: {
    'omdb-header': Header,
    'omdb-content': Content,
    'omdb-footer': Footer
  }
}
</script>

<style>
:root {
  --font-family-1: 'Roboto Condensed', sans-serif;
  --font-family-2: 'Nunito', sans-serif;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 0px;
}
</style>
