<template>
  <div class="header">
    <div class="nav">
      <img class="logo" :src="logo">
      <nav class="menu">
        <a href="#">Browse</a>
        <a href="#">Community</a>
        <a href="#">Docs</a>
        <a href="#">Contact</a>
      </nav>
    </div>
  </div>
</template>

<script>
import logo from '../assets/movito.png';

export default {
  name: 'Header',
  data() {
    return {
      logo
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
.header {
  background-color: rgb(10, 25, 41);
  color: #fff;
}

.logo{
  cursor: pointer;
}

.nav {
  max-width: 1400px;
  padding: 20px 0px;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  margin: 0 auto;
}

.menu {
  display: flex;
  justify-content: center;
  align-items: center;
}
.menu a {
  color: #ffffff;
  text-decoration: none;
  font-family: var(--font-family-2);
  font-size: 1.1rem;
  padding: 20px;
}
.menu a:hover {
  background-color: rgba(255, 255, 255, 0.1);
}

@media only screen and (max-width: 1200px) {
  .nav {
    margin: 0 auto;
    padding: 20px 40px;
  }
}
@media only screen and (max-width: 800px) {
  .nav {
    display: flex;
    justify-content: center;
  }
  .menu {
    display: none;
  }
}
</style>
