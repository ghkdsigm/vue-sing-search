<template>
    <div class="container">
        <!-- <input type="text" v-model="title" class="form-control" placeholder="노래제목이나 가수를 검색해주세요." @keyup.enter="apply"/>
        <div class="selects">
            <select v-for="filter in filters" v-model="$data[number]"  :key="filter.name" class="form-select">
                <option v-if="filter.name === 'number'" value="">
                    선택
                </option>
                <option v-for="item in filter.items" :key="item">
                    {{item + '개씩'}}
                </option>
            </select>
        </div>
        <div class="btn btn-primary" @click="apply">
            검색
        </div> -->
        <div class="search-bar">
            <input type="text" @keyup.enter="searchedVideos" placeholder="가수나 노래를 검색해주세요.">
        </div>
    </div>
</template>

<script>
import axios from 'axios'

const YOUTUBE_API_KEY = 'AIzaSyDm1pVozp2zRcgr3S-8BrKrHDokuPJCsKw'
const YOUTUBE_API_URL = 'https://www.googleapis.com/youtube/v3/search'
export default {
    //data(){
       // return {
            //number:10,            
            //filters:[
              //  {
               //     name:'number',
                //    items:[10,20,30]
                //}
                
            //]
       // }
   // },
    name: 'Search',
    methods:{
        async searchedVideos(event) {
            const keyword = event.target.value + '태진 노래방'
            const config = {
                params: {
                    part: 'snippet',
                    type: 'video',
                    q: keyword,
                    key: YOUTUBE_API_KEY,
                },
            }
            //console.log(keyword)

            //axios.get(YOUTUBE_API_URL, config)

            const response = await axios.get(YOUTUBE_API_URL, config)
            //console.log(response)
            const videoList = response.data.items
            // 부모한테 올리기 케밥케이스 비디오리스트를 app.vue methods 에넘긴다.
            this.$emit('searched-videos', videoList)
        },
    }
}
</script>

<style lang="scss" scoped>
@import "~/scss/main";
.container {
    display: flex;
    > * {
        margin-right:10px;
        &:last-child{
            margin-right:0;
        }
    }
    .search-bar { 
        width:100%;
        input {    width: 100%;    padding: 0.5rem;    font-size: 2rem 1rem;}
    }
    // .selects {
    //     display:flex;
    //     select{
    //         width:120px;
    //         margin-right:10px;
    //         &:last-child {
    //             margin-right:0;
    //         }
    //     }
    // }
    // .btn {
    //     width:120px;
    //     height:50px;
    //     font-weight: 700;
    //     flex-shrink: 1;
    //     line-height: 34px;
    //     font-size: 18px;
    // }

}

</style>