<template>
  <div class="home">
    <div class="container">
      <img src="../assets/CryptoBackground2.jpeg" />
      <h1 class="intro">Welcome to Crypto Marketplace</h1>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: 'HomeView',
  // components: {
  //   HelloWorld
  // }
}
</script>

<style>
img {
  width: 100%;
}

.container {
  position: relative;
}

.intro {
  position: absolute;
  bottom: 40%;
  left: 20%;
  font-size: 56px;
  color: yellow;
  text-shadow: -1px -1px 0 #000, 1px -1px 0 #000, -1px 1px 0 #000, 1px 1px 0 #000;
}
</style>
