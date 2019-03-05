<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">Calculator</router-link> |
      <router-link to="/about">About</router-link>
    </div>
    <router-view/>
  </div>
</template>

<style lang="scss">
* {
  box-sizing: border-box;
}

body {
  padding: 0;
  margin: 0;
}

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
#nav {
  padding: 30px;
  a {
    font-weight: bold;
    color: #2c3e50;
    &.router-link-exact-active {
      color: #42b983;
    }
  }
}

.ref {
  font-size: 14px;

  a {
    background-color: pink;
    color: #ff2047;
    text-decoration: none;

    &:hover {
      background-color: darkmagenta;
    }
  }
}
</style>
