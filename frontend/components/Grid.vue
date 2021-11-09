<template>
  <div class="container">
    <div class="row" v-editable="blok">
      <!-- <pre>{{blok}}</pre> -->
      <div :class="'col-lg-' + blok.block_left_size">
        <component
          v-for="blok in blok.block_left"
          :key="blok._uid"
          :blok="blok"
          :is="blok.component" 
        />
      </div>
      <div :class="'col-lg-' + blok.block_right_size">
        <component
          v-for="blok in blok.block_right"
          :key="blok._uid"
          :blok="blok"
          :is="blok.component" 
        />
      </div>
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
  .row{
  }
</style>