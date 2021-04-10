<template>
    <ul class="list-group  col-md-4">
        <videoListItem 
        v-for="video in videos" 
        v-bind:key="video.etag" 
        v-bind:video="video"
        v-on:videoSelect="onVideoSelect">
        
        </videoListItem>
    </ul>
</template>

<script>
import videoListItem from './videoListItem'
export default {
    name: 'VideoList',
    components:{
        videoListItem
    },
    props:{
        videos: Array
    },
    methods:{
        onVideoSelect(video){
            this.$emit('videoSelect', video);
        }
    }
}
</script>


<style>

</style>