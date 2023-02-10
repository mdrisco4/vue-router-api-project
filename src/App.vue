<template>
  <nav>
    <router-link to="/" class="router-link">Home</router-link> |
    <router-link to="/market" class="router-link">Market</router-link> |
    <router-link to="/about" class="router-link">About</router-link>
  </nav>
  <router-view/>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  background-color: black;
}

.router-link {
  color: white;
}

nav {
  padding: 30px;
  text-align: center;
  color: white;
}

@media only screen and (min-width: 500px) {
  nav {
    font-size: 20px;
  }
}

@media only screen and (min-width: 630px) {
  nav {
    font-size: 25px;
  }
}

@media only screen and (min-width: 768px) {
  nav {
    font-size: 32px;
  }
}

@media only screen and (min-width: 850px) {
  nav {
    font-size: 36px;
  }
}

@media only screen and (min-width: 960px) {
  nav {
    font-size: 42px;
  }
}

@media only screen and (min-width: 1100px) {
  nav {
    font-size: 49px;
  }
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

@media only screen and (min-width: 500px) {
  nav a {
    font-size: 20px;
  }
}

@media only screen and (min-width: 630px) {
  nav a {
    font-size: 25px;
  }
}

@media only screen and (min-width: 768px) {
  nav a {
    font-size: 32px;
  }
}

@media only screen and (min-width: 850px) {
  nav a {
    font-size: 36px;
  }
}

@media only screen and (min-width: 960px) {
  nav a {
    font-size: 42px;
  }
}

@media only screen and (min-width: 1100px) {
  nav a {
    font-size: 49px;
  }
}

nav a.router-link-exact-active {
  /* color: #42b983; */
  color: greenyellow;
}
</style>
