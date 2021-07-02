<template>
  <div id="banner">
    <h1>Make Your Burguer</h1>
  </div>
</template>

<script>
export default {
  name: 'Banner'
}
</script>

<style scoped>
#banner {
  background-image: url('/img/burger.jpg');
  background-position: 0 -400px;
  background-size: cover;
  height: 350px;
  display: flex;
  align-items: center;
  justify-content: flex-start;
}

#banner h1 {
  color: white;
  text-align: center;
  padding: 20px 40px;
}
</style>