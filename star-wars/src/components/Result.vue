<template>
  <div class="results d-flex justify-content-center row mt-5">
    <div v-for="(item, i) in filmList" :key="i" class="search-result col-4 text-left pt-5 px-5 m-1" >
      <h1 class="m-0"> {{item.title}} </h1>
      <small class="text-muted"> Producer: {{item.producer}}</small>
      <br>
      {{item.opening_crawl}}
      <hr>
      <small class="text-muted">Release Date: {{item.release_date}}</small>

      <!-- <a href="" class="text-center nav-link text-dark">View More...</a> -->
      <a v-bind:href="'#expanded' + i" v-on:click="searchCharacters(item)" data-toggle="collapse" aria-expanded="true" aria-controls="collapseOne" class="text-center nav-link text-dark">View More...</a>
      <div v-bind:id="'expanded' + i" class="collapse"> 
        <Small><b>Director: </b>{{item.director}}</Small> 
        <br>
        <Small><b>Episode Number:</b> {{item.episode_id}}</Small>
        <br>
        <small><a v-bind:href="item.url"> {{item.url}} </a></small>
        <br>
        <small class="font-weight-bold">Characaters:</small>
        <div v-for="(char,i) in characters" :key="i">
          <small>{{char}}</small>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import EventBus from '../EventBus'
// import ViewMore from './ViewMore'

export default {
  data () {
    return  {
      result: [],
      filmList: [],
      characters: []
    }
  },
  mounted() {
    EventBus.$on('LIST_SENT',  (resultData)=>{
      this.filmList = resultData
    })
  },
  methods:  {
    searchCharacters: function(charlist)  {
      this.characters.length = 0
      console.log(charlist.characters.length)
      for (let i = 0; i < charlist.characters.length; i++) {
        axios.get(charlist.characters[i])
          .then((response)=>{
            this.characters.push(response.data.name)
          })
      }
    }
  }
  // components: {
  //   ViewMore
  // }
}

</script>

<style lang="css" scoped>

  .search-result  {
    background-color: rgba(238, 238, 238,  0.9);
    color: #000000;
  }
</style>