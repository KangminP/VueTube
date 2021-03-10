<template>
    <div>
        <ul class="list-group mt-5">
            <VideoDetail 
                v-for="video in videos"
                :key="video.etag"
                :video="video"
                />
        </ul>
    </div>
</template>

<script>
import VideoDetail from './VideoDetail.vue'

export default {
    name: 'Videoitem',
    components: {
        VideoDetail,
    },
    props: {
        videos: Array,
    }
}
</script>

<style>

</style>