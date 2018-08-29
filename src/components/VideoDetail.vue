<template>
  <div v-if="video">
    <div class="embed-responsive embed-responsive-16by9">
      <iframe v-bind:src="videoUrl" />
    </div>
    <!-- v-if: if right side is falsy, ie, null is falsy, the div will not show -->
    <div class="details">
      <h4>{{ video.snippet.title }}</h4>
      <p>{{ video.snippet.description }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'VideoDetail',
  props: ['video'],
  computed: {
    videoUrl(){
      const videoId = this.video.id.videoId;
      return 'https://www.youtube.com/embed/' + videoId;
      // aka const { videoId } = this.video.id;
      // return `https://www.youtube.com/embed/${videoId}`
    }
  }
}
</script>

<style scoped>
.details {
  margin-top: 10px;
  padding: 10px;
  border: 1px solid #ddd;
  border-radius: 10px;
}
</style>
