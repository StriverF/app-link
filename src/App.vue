<template>
  <div id="nav">
    <!-- <router-link to="/">Home</router-link> |
    <router-link to="/about">About</router-link> -->
    <H1>Goin PatPat App Or Website</H1>
  </div>
  <router-view/>
</template>

<style lang="less">
*{
  // box-sizing: border-box;
  font-weight: 400;
  padding: 0;
  margin: 0;
  text-decoration: none;
  box-sizing: border-box;
  font-style: normal;
  -webkit-tap-highlight-color: rgba(255, 255, 255, 0);
  outline: none;
  border: none;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
H1 {
  font-size: 18px;
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
</style>
