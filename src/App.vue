<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <!-- <ToDoPage/> -->
    <ArchivePage/>
    <!--<task-list></task-list>-->
  </div>
</template>

<script>
//import HelloWorld from './components/HelloWorld.vue'
//mport ToDoPage from './pages/ToDoPage.vue'
import ArchivePage from './pages/ArchivePage'

export default {
  name: 'App',
  components: {
    ArchivePage
  }
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
