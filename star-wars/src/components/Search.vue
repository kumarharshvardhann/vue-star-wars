<template>
  <div class="search-box">
    <h3 class="title h1 ">Search in Star Wars Universe</h3>
    <div class="d-flex justify-content-center rgb">
      <input v-on:keyup.enter="validate" class="w-25 fi form-control bg-warning" v-model="search" type="text" placeholder="Search Movies..." v-focus>
      <input v-on:click="validate" class="fi srch btn btn-danger ml-3" type="button" name="Search" value="Search">
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import EventBus from '../EventBus'
import { log } from 'util';

export default {
  name: 'Search',
  data  ()  {
    return  {
      search: "",
    }
  },
  methods:  {
    validate  ()  {
      var url = 'https://swapi.co/api/films/?search=' + this.search
      if (this.search == "") {
        alert("Please enter valid inputs!")
      }
      else  {
        axios.get(url)
        .then((response)=>{
          this.process(response.data.results)
        })
        .catch(() => {
          console.log(" Sorry no movies found!")
        })        
      }
    },

    process (list)  {
      EventBus.$emit('LIST_SENT',list)
    }
  },

  directives: {
  focus: {
      inserted: function (el) {
        el.focus()
      }
    }
  }
}
</script>

<style lang="css" scoped>
  .fi  {
    /* margin-top: 10%; */
  }

  .srch  {
    width: 5%;
  }

  .title  {

    margin-top: 4%;
    font-family: "Renner* Medium";
  }
</style>
