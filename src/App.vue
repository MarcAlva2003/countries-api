<template>
  <div>
    <AppHeader/>
    <router-view></router-view>
  </div>
</template>

<script>
import AppHeader from './components/AppHeader.vue'

export default {
  name: 'App',
  components:{
    AppHeader
  }
}
</script>

<style>
html{
    font-size: 62.5%;
    box-sizing: border-box;
}
*, *:before, *:after{
    box-sizing: inherit;
}
body{
    font-size: 16px; /*1rem = 10px*/
    background-color: rgba(230, 230, 230, 0.712);
  font-family: 'Open Sans', sans-serif;
}
a{
    text-decoration: none;
}
h1,h2,h3,h4,h5,a,p, body{ 
  margin: 0;
  padding: 0;
}
</style>
