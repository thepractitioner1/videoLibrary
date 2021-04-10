<template>
  <li class="list-group-item" v-on:click="onVideoSelect">
    <img v-bind:src="thumbnailUrl" class="mr-3" />
    <div class="media-body">
      {{ video.snippet.title }}
    </div>
  </li>
</template>

<script>
export default {
  name: "videoListItem",
  props: {
    video: Object,
  },
  computed: {
    thumbnailUrl() {
      return this.video.snippet.thumbnails.default.url;
    },
  },

  methods:{
    onVideoSelect(){
      this.$emit('videoSelect', this.video);
    }
  }
};
</script>

<style scoped>
  li{
    display: flex;
    cursor: pointer;
  }

  li:hover{
    background-color: #eee;
  }
</style>