<template>
  <div class="home">
    <div class="videos">
      <div class="video" v-for="(video, index) in videos" :key="index">
        <img :src="generateThumbnailUrl(video.id)" alt="">
        <h2> {{ video.name }} </h2>
        <p>{{ video.desc }}</p>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import axios from 'axios'

export default {
  name: 'Videos',
  data(){
    return {
        videos: []
    }
  },
  computed: {
      language: function() {
          return this.$route.params.lang;
      }
  },
  methods: {
    generateThumbnailUrl: function(id) {
        return 'https://i3.ytimg.com/vi/' + id + '/default.jpg';
    },
    getVideos: function(){
          if(this.language == 'en'){
            axios.get('https://api.npoint.io/934b10cb1c4422d2920b')
            .then((res) => {
                this.videos = res.data.Videos;
            }) 
      } else if(this.language == 'rs'){
            axios.get('https://api.npoint.io/68ced50d9a7d64844463')
          .then((res) => {
            this.videos = res.data.Videos;
          })
      } else {
          alert('nothing for this language')
      }
    }

  },
  mounted(){
      this.getVideos();
  },
  watch:{
      language: function(){
          this.getVideos();
      }
  }
}
</script>
