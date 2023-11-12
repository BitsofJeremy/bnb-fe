<template>
  <HelloWorld msg="Hello" />
</template>

<script>
import axios from 'axios'
import HelloWorld from './components/HelloWorld.vue'

var options = {
  method: 'GET',
  url: 'http://127.0.0.1:8000/api/auctions/',
  headers: {Authorization: 'Basic YWRtaW46c3BpZGVybWFu'}
};

let auction_list;

export default {
  name: 'BNB',
  components: {
    HelloWorld
  },
  mounted () {
    axios.request(options).then(function (response) {
      auction_list = response.data.results;
      console.log(response.data);

      console.log(auction_list);
      for (let i in auction_list) {console.log(i);}


      }).catch(function (error) {
        console.error(error);
      });
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
</style>
