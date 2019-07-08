<template>
  <div id="app">
    <search/>
    <result/>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import Search from './components/Search'
import Result from './components/Result'
// import axios from 'axios'
import { log } from 'util';

export default {
  name: 'app',
  data: function  ()  {
    return  {
      
    }
  },
  components: {
    Search,
    Result    
  }
}

// axios.get('https://jsonplaceholder.typicode.com/todos/1')
//   .then(response => console.log(response))

</script>

<style>
html, body {
  height: 100%;
  width: auto;
  overflow: hidden;
}

body {
  background-image: url("./assets/bg.jpg");
  background-repeat: no-repeat;
  background-size: fit;
}

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: white;
  height: 100%;
  overflow: scroll;
  
}

</style>
