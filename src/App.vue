<template>
  <div class="container">
    <div class="jumbotron">
      <h1>YouTube Viewer</h1>
    </div>
    <SearchBar
      v-on:termChange="onTermChange">
    </SearchBar>
    <div class="row">
      <VideoDetail v-bind:video="selectedVideo"  />
      <VideoList
      @videoSelect="onVideoSelect" v-bind:videos="videos">
      </VideoList>
    </div>

  </div>
  <!-- it is also ok to write as <SearchBar @termChange="onTermChange">... v-bind:videos="videos" can also be written as :videos="videos" -->
  <!-- <VideoList v-bind:videos="videos">.. the left 'videos' is what we are now calling the props we're passing down. The right 'videos' refers directly to the data property videos from our script -->
</template>

<script>
  import axios from 'axios';
  import SearchBar from './components/SearchBar';
  import VideoList from './components/VideoList';
  import VideoDetail from './components/VideoDetail';
  const API_KEY = require('./../env').apiKey;
  //input api key above;

  export default {
    name: 'App',
    components: {
      //es6 says, since the keyvalue pairs are identical, you can just write SearchBar, but for clarity sake I included both key & value
      SearchBar: SearchBar,
      VideoList: VideoList,
      VideoDetail: VideoDetail,
    },
    // data properties are where you want the View to update based on new data, ie {{ videos.length }} in template refers to data's video property
    data() {
      return {
        videos: [],
        selectedVideo: null
      };
    },
    methods: {
      onVideoSelect(video) {
        this.selectedVideo = video;
      },
      onTermChange(searchTerm){
        axios.get('https://www.googleapis.com/youtube/v3/search', {
          params: {
            key: API_KEY,
            type: 'video',
            part: 'snippet',
            q: searchTerm
          }
        }).then(response => {
          this.videos = response.data.items
        });
      }
      // can also be seen as onTermChange: function(searchTerm){};
      // searchTerm is the second arg from onInput, aka event.target.value;
    }
  };
</script>
<style scoped>
  .jumbotron {
    text-align: center;
  }
</style>
