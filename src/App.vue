<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link> |
      <router-link to="/portfolio">Portfolio</router-link> |
      <router-link to="/reviews">Review</router-link>
    </div>
    <router-view/>
    <div class='footer'>
      <a class = 'footer-item' href='https://github.com/MichaelCh-svg/latvija.git'> Git Code</a>
    </div>
  </div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
.footer{
    display:flex;
    justify-content: center;
    height: 100px;
    background-color:olive;
}
.footer-item{
    align-self:center;
}
#nav {
  padding: 30px;
  border-style:solid;
  border-width: 3px;
  background-color:olive;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
