<template>
    <Headline />
    <Search @searched-videos="searchedVideos" />
   
    <section class="container">
        <VideoListItemDetail  v-if="isVideoSelected" :video="selectedVideo" />
        <VideoList :videoList="videoList"  @select-video="selectVideo" />
    </section>
    
</template>

<script>
import Headline from '~/components/Headline'
import Search from '~/components/Search'
import VideoList from '~/components/VideoList'
import VideoListItemDetail from '~/components/VideoListItemDetail'

export default {
    name: 'App',
    components:{
        Headline,
        Search,
        VideoList,
        VideoListItemDetail        
    },
    data() {
        return {
            videoList: [],
            selectedVideo: {},
            isVideoSelected:false,
        }
    },
    methods: {
        searchedVideos(videoList) {
        this.videoList = videoList
 
        },
        selectVideo(video) {
        console.log(video)
        this.selectedVideo = video
        this.isVideoSelected = true
        },
    },
    
}
</script>

<style>
header,section {
  width: 80%;
  margin: 0 auto;
  padding: 4rem 0;
}
section {
  display:flex;
}
</style>