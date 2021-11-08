<template>
  <div class="container">
    <div class="banner-sportstest my-4 p-4 d-flex justify-content-center align-items-center" v-editable="blok" v-bind:style="{ 'background-image': 'url(' + blok.bg_image + ')' }">
      <h3 class="mb-0 mx-3">{{blok.title}}</h3>
      <a href="#" class="button px-4 py-3">{{blok.button_title}}</a>
    </div>
  </div>
  
</template>
 
<script>
export default {
  props: {
    blok: {
      type: Object,
      required: true
    }
  }
}
</script>

<style lang="scss" scoped>
  .banner-sportstest{
    background-size: cover;
    background-repeat: no-repeat;
    background-position: center center;
    h3{
      color: white;
    }
    .button{
      background-color: $primary;
      color: white;
      font-family: $headingstack;
      border-radius: 4px;
      font-size: 18px;
      line-height: 1;
      text-transform: uppercase;
    }
  }
</style>