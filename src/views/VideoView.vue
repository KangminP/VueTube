<template>
    <div class="container mt-4">
        <h1 class="mt-5"><img src="../assets/video.png" width="60px"> 영화 예고편 검색</h1>
        <VideoSearch @search-video="searchVideo"/>
        <VideoItem :videos="videos"/>
        <img src="../assets/video_people.jpg" v-if="!videos" class="mt-5 mb-5">
    </div>
</template>

<script>
import axios from 'axios'
import _ from 'lodash'

import VideoSearch from '../components/VideoSearch.vue'
import VideoItem from '../components/VideoItem.vue'

const API_URL = 'https://www.googleapis.com/youtube/v3/search'
const API_YOUTUBE_KEY = process.env.VUE_APP_YOUTUBE_DAYA_API_KEY

export default {
    name: 'VideoView',
    components: {
        VideoSearch,
        VideoItem,
    },
    data() {
        return {
            videos: null,
        }
    },
    methods: {
        searchVideo(keyword) {
            if (keyword.trim()) {
                axios.get(API_URL, {
                    params: {
                        key: API_YOUTUBE_KEY,
                        part: 'snippet',
                        q: `${keyword} trailer`,
                        type: 'video',
                    }
                })
                    .then(res => {
                        res.data.items.forEach(item => {
                            item.snippet.title = _.unescape(item.snippet.title)
                        })
                        this.videos = res.data.items
                    })
                    .catch(err => console.error(err))
            }
        }
    }
}
</script>

<style>

</style>