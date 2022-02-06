<template>
  <div v-if="videoList.length">
      <VideoListItem
        v-for="video in videoList"
        :video="video"
        :key="video.id.videoId"
        @select-video="selectVideo"
      />
  </div>
</template>

<script>
import VideoListItem from '~/components/VideoListItem'


export default {
    name: 'VideoList',
    components:{
        VideoListItem,
    },
    props: {
        videoList: Array,
    },
    methods: {
        selectVideo(video) {
            this.$emit('select-video', video)
        },
    },
}
</script>

<style>
.videoList {
  width: 30%;
}
.videoListItem {
  display:flex;
}
.videoListItem__title {
  font-size:1.25rem;
  font-weight:bold;
}
</style>