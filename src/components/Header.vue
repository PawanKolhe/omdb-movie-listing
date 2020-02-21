<template>
  <div class="header">
    <div class="nav">
      <img :src="logo">
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

.nav {
  max-width: 1200px;
  padding: 20px 80px;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
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
}
</style>
