<template>
  <ul class="list-group col-md-4">
    <VideoListItem
    v-for="video in videos"
    v-bind:video="video"
    :key="video.etag"
    @videoSelect="onVideoSelect"
    >
  </VideoListItem>
  <!-- above, v-bind:video="video", the right "video" refers to the 'video' in our v-for loop, not the props below -->
  <!-- etag is an identitifying key provided by Youtube -->
</ul>
</template>

<script>
import VideoListItem from './VideoListItem';
export default {
  name: 'VideoList',
  components: {
    VideoListItem: VideoListItem
  },
  props: ['videos'],
  methods: {
    onVideoSelect(video){
      this.$emit('videoSelect', video);
    }
  }
}
</script>

<style>
</style>
