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
  font-size: 20px;
  color: yellow;
  text-shadow: -1px -1px 0 #000, 1px -1px 0 #000, -1px 1px 0 #000, 1px 1px 0 #000;
}

@media only screen and (min-width: 500px) {
  .intro {
    font-size: 28px;
  }
}

@media only screen and (min-width: 550px) {
  .intro {
    font-size: 35px;
  }
}

@media only screen and (min-width: 640px) {
  .intro {
    font-size: 42px;
  }
}

@media only screen and (min-width: 720px) {
  .intro {
    font-size: 48px;
  }
}

@media only screen and (min-width: 768px) {
  .intro {
    font-size: 56px;
  }
}

@media only screen and (min-width: 850px) {
  .intro {
    font-size: 63px;
  }
}

@media only screen and (min-width: 980px) {
  .intro {
    font-size: 72px;
  }
}

@media only screen and (min-width: 1100px) {
  .intro {
    font-size: 81px;
  }
}
</style>
