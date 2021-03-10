<template>
    <li class="list-group-item list-group-item-action">
        <h4 class="mx-auto">{{ video.snippet.title }}</h4>
        <iframe
            width="560" 
            height="315"
            :src="videoUrl" 
            class="embed-responsive-item" 
            frameborder="0" 
            allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" 
            allowfullscreen
        ></iframe>
    </li>
</template>

<script>
export default {
    name: 'VideoDetail',
    props: {
        video: Object,
    },
    computed: {
        videoUrl() {
            return `https://www.youtube.com/embed/${this.video.id.videoId}`
        }
    }
}
</script>

<style>

</style>