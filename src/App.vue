<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png"><br>
    <router-link to="/">Organize</router-link>
    <router-link to="/archive">Archive</router-link>
    <router-view/>
  </div>
</template>

<script>
export default {
  name: 'App'
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
#app>img{
  transition: .8s;
}
#app>img:hover{
  transform: rotate(360deg);
  transition: .8s;
}
</style>
