<template>
  <img id = "tree" alt="Tree Logo" src="./assets/LogoApp.webp">
  <div>
    <HomePage/> 
  </div>
</template>

<script>
import HomePage from '@/pages/HomePage.vue';


export default 
{
  name: 'App',
  components:
  {
    HomePage,
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  margin-top: 60px;
}
#tree
{
  height: 200px;
  width: 200px;
}

</style>
