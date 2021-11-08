<template>
  <div class="page-header-home" v-editable="blok">
    
    <div class="container">
      <div class="holder-title d-inline-block pl-5" v-if="!blok.only_background">
        <h1 class="m-0" v-html="formatHead(blok.title)" :class="blok.show_subtitle ? 'small' : ''"></h1>
        <div class="subtitle" v-if="blok.show_subtitle" v-html="formatHead(blok.subtitle)"></div> 
      </div>
    </div>
  </div>
  
</template>
 
<script>
import VideoPlayer from 'nuxt-video-player'
require('nuxt-video-player/src/assets/css/main.css')
export default {
  components: {
    VideoPlayer
  },
  props: {
    blok: {
      type: Object,
      required: true
    }
  },
  methods: {
    formatHead(title){
      let returnStr = "";
      if (!title) {
        return returnStr;
      }
      const txtArr = title.split("**");
      txtArr.forEach((txt, i) => {
        i % 2 !== 0 ?
        (returnStr += "<span>" + txt) :
        (returnStr += "</span>" + txt);
      });
      return returnStr;
    }
  }
}
</script>

<style lang="scss">
  .page-header-home{
    .background{
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 350px;
      background-size: cover;
      background-repeat: no-repeat;
      background-position: center center;
      overflow:hidden;
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
          position: absolute;
          left: 50%;
          width: 100%;
          height: 100%;
          top: 50%;
          transform: translate(-50%,-50%);
        }
      }
    }
    &.fill{
      padding-bottom: 140px;
      min-height: 413px;
    }
    &.bottom{
      padding-bottom: 140px;
      min-height: 413px;
      h1{
        background-color: $secondary;
        position: absolute;
        bottom: 0;
        left: 0;
        padding: 0.75rem 1.25rem;
      }
    }
    .holder-title{
      padding: 72px 0px;
      position: relative;
      h1{
        color: white;
        line-height: 1;
        text-transform: uppercase;
        &.small{
          font-size: 90px;
        }
        span{
          display: block;
        }
      }
      .subtitle{
        font-size: 32px;
        font-family: $headingstack;
        color: white;
        text-align: right;
        line-height: 1;
        span{
          color: $primary
        }
      }
    }
    
  }
  
</style>
