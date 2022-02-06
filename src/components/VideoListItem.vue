<template>
    <div class="container">
        <div @click="selectVideo" class="videoListItem">
        <!-- #3-1 -->
            <img :src="thumbnailUrl(video)" alt="">
            <div>
            <!-- #5-1 -->
            <div class="videoListItem__title">{{ video.snippet.title }}</div>
            <div class="videoListItem__channelTitle">{{video.snippet.channelTitle}}</div>
            <!-- <div class="videoListItem__description">{{video.snippet.description}}</div> -->
            </div>
        </div>
    </div>  
</template>

<script>
import _ from 'lodash'

export default {
    name: 'VideoListItem',
    props: {
        video:Object,
    },
    methods: {
        // #3
        thumbnailUrl(video) {
            return video.snippet.thumbnails.high.url
    },
    // #4
        selectVideo(){
            this.$emit('select-video',this.video)
        }
    },
    // #5
    // filters: {
    //     unescape(v){
    //     return _.unescape(v)
    //     }
    // }
}
</script>

<style lang="scss" scoped>
.videoListItem {
  /* display:flex; */
  height: 190px;
  padding:10px 5px;
  margin-bottom: 5px;
  border: 3px solid transparent;
  &:hover {
      cursor:pointer;
      border: 3px solid royalblue;
      
      //padding:5px 0;
  }
  img {
      margin:0 15px;
  }
}
.videoListItem__title {
  font-size:1.25rem;
  font-weight:bold;
}

</style>