<template>
  <ul class="list-group">
    <VideoListItem
      v-for="video in videos"
      v-bind:video="video"
      :key="video.etag"
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
  props: ['videos']
}
</script>

<style>
</style>
