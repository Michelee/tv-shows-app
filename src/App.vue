<template>
  <nav>
    <h1 class="pageTitle">TV Shows Info</h1>
  </nav>
  <router-view />
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  background-color: black;
}

body {
  margin: 0;
}

.pageTitle {
  font-size: 30px;
  margin-right: 30px;
  color: white;
  margin: 0;
}

nav {
  padding: 30px;
  display: flex;
  align-items: center;
  margin-bottom: 20px;
}

nav a {
  font-weight: bold;
  color: #808080;
}

nav a.router-link-exact-active {
  color: #42b983;
}
</style>
