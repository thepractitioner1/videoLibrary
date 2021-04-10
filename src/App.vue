<template>
  <div id="app" class="container">
    <searchBar v-on:termChange="onTermChange"></searchBar>
    <div class="row">

    <videoDetail v-bind:video="selectedVideo"></videoDetail>
    <videoList v-bind:videos="videos" v-on:videoSelect="onVideoSelect"></videoList>
    
    </div>
  </div>
</template>

<script>
import axios from "axios";
import searchBar from "./components/searchBar.vue";
import videoList from "./components/videoList";
import videoDetail from "./components/videoDetail"

export default {
  name: "App",
  components: {
    searchBar,
    videoList,
    videoDetail
  },

  data: function () {
    return {
      videos: [],
      selectedVideo: null
    };
  },
  methods: {
    onTermChange(searchTerm) {
      axios
        .get("https://www.googleapis.com/youtube/v3/search", {
          params: {
            key: API_KEY,
            type: "video",
            part: "snippet",
            q: searchTerm,
          },
        })
        .then((response) => {
          this.videos = response.data.items
        });
    },

    onVideoSelect(video){
      this.selectedVideo = video;
    }
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;

  color: #2c3e50;
}
</style>
