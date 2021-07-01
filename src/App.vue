<template>
  <NavBar :applogo="applogo" :alt="appname"/>
  <router-view/>
  <Footer />
</template>

<script>
import NavBar from './components/NavBar.vue'
import Footer from './components/Footer.vue'

export default {
  name: 'App',
  components: {
    NavBar,
    Footer
  },
  data() {
    return {
      applogo: '/img/logo.png',
      appname: 'Burger'
    }
  }
}
</script>

<style>
@font-face {
  font-family: Inter;
  src: url('/fonts/Inter-VariableFont.ttf');
}

* {
  font-family: Inter, sans-serif;
}

body {
  margin: 0px;
  box-sizing: border-box;
}

h1 {
  text-align: center;
}

.main-container {
  margin: 50px;
  min-height: 250px;
}
</style>