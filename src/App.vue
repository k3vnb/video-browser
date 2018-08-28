<template>
  <div>
    <SearchBar v-on:termChange="onTermChange"></SearchBar>
    Hello from Vue video-browser app
  </div>
  <!-- it is also ok to write as <SearchBar @termChange="onTermChange"> -->
</template>

<script>
  import axios from 'axios';
  import SearchBar from './components/SearchBar';
  const API_KEY = xxx;
  //input api key above;

  export default {
    name: 'App',
    components: {
      //es6 says, since the keyvalue pairs are identical, you can just write SearchBar, but for clarity sake I included both key & value
      SearchBar: SearchBar
    },
    methods: {
      onTermChange(searchTerm){
        axios.get('https://www.googleapis.com/youtube/v3/search', {
          params: {
            key: API_KEY,
            type: 'video',
            part: 'snippet',
            q: searchTerm
          }
        }).then(response => console.log(response));
      }
      // can also be seen as onTermChange: function(searchTerm){};
      // searchTerm is the second arg from onInput, aka event.target.value;
    }
  };
</script>
