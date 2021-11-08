<template>
    <div class="page-header-background" :style="[imageUrl  ? {'background': 'url(' + imageUrl + ') center no-repeat'} : {'background': '#000'}]">
        <div class="video">
            <video-player class="video zwemmen d-none d-md-block" :src="videoUrl"/>
            <!-- <video v-if="videoUrl" id="videoPlayer" autoplay loop muted class="video zwemmen d-none d-md-block">
                <source :src="videoUrl" type="video/mp4">
            </video> -->
        </div>
        <img class="bottom-bar" src="@/assets/img/bottom_header.png"/>
    </div>
</template>
<script>
import VideoPlayer from 'nuxt-video-player'
require('nuxt-video-player/src/assets/css/main.css')
export default ({
    components: {
        VideoPlayer
    },
    data(){
        return{
            currentPage: '',
            videoUrl: '',
            imageUrl: ''
        }
    },
    methods: {
        setMedia(routeName){
            console.log('setting media for page:', routeName)
            switch(routeName) {
              case 'zwemmen':
                this.videoUrl = require('@/assets/videos/pool_water_1.mp4')
                break;
              case 'schaatsen':
                this.videoUrl = require('@/assets/videos/schaats_cinemagraph.mp4')
                break;
              default:
                this.videoUrl = require('@/assets/videos/voetbal-cinemagraph-v2.mp4')
            }
        }
    },

    watch: {
      '$route' (to, from) {
        this.currentPage = to.name
        this.setMedia(to.name)
        
      }
    },

    created(){
        console.log(this.$route.path)
        this.setMedia(this.$route.name)
    }
})
</script>

<style lang="scss" scoped>
    .page-header-background{
        overflow: hidden;
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 350px;
        background-size: cover;
        background-repeat: no-repeat;
        background-position: center center;
        z-index: -1;
        @include tablet{
            height: 400px;
        }
        @include desktop-up{
            height: 500px
        }
        .bottom-bar{
            position: absolute;
            bottom: 0;
            left: 0;
            width: 100%;
            height: 60px;
            z-index: 0;
        }
        .video{
            position: relative;
            height: 500px;
            width: 100%;
            .v-player{
                position: relative;
                top: 50%;
                transform: translate(0,-50%);
            }
        }
    }
</style>
