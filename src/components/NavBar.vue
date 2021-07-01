<template>
  <div id="nav">
    <router-link to="/" id="logo-url">
      <img :src="applogo" :alt="alt" id="logo">
    </router-link>
    <router-link to="/">Home</router-link> 
    <router-link to="/pedidos">Pedidos</router-link>
  </div>
</template>

<script>
export default {
  name: 'NavBar',
  props: ['applogo', 'alt']
}
</script>

<style scoped>
  #nav {
    border-bottom: 1px solid rgba(0, 0, 0, 0.12);
    padding: 15px 50px;
    display: flex;
    justify-content: flex-end;
    align-items: center;
  }

  #nav #logo-url {
    margin-right: auto;
  }

  #logo {
    height: 40px;
    width: 40px;
  }

  #nav a {
    text-decoration: none;
    color: #fd8f31;
    margin: 0px 12px;
    transition: 0.5s;
  }

  #nav a:hover {
    color: #fccf3f;
  }
</style>