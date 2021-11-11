<template>
  <div class="activities" v-editable="blok">
    <h5>Activiteiten</h5>
    <div class="activity-block-items d-flex row" >
      <div class="col-6" v-for="item in activities" :key="item.id">
        <NuxtLink :to="item.full_slug" class="item d-flex">
          <div class="image"></div>
          <h4 class="px-2 py-2">{{ item.name }}</h4>
        </NuxtLink>
      </div>
    </div>
  </div>
  
</template>

<script>
import axios from "axios";
export default {
  props: {
    blok: {
      type: Object,
      required: true,
    },
  },

  data() {
    return {
      activities: [],
    };
  },

  created() {
    var data = {
      version: "draft",
      starts_with: "activities/",
      token: process.env.STORYBLOK_TOKEN,
      excluding_slugs: "activities/",
    };
    var config = {
      method: "get",
      url: `https://api.storyblok.com/v2/cdn/stories/`,
      headers: {
        "Content-Type": "application/json",
        Accept: "application/json",
      },
      params: data,
    };
    axios(config).then((response) => {
      // console.log(response);
      this.activities = response.data.stories;
    });
  },
};
</script>

<style lang="scss" scoped>
.activity-block-items {
  margin-right: -6px;
  margin-left: -6px;
  .col-6,
  .col-4,
  .col-3 {
    padding-left: 6px;
    padding-right: 6px;
  }
  .col-12 {
    padding-left: 0;
    padding-right: 5px;
  }
  .item {
    background-color: #026596;
    margin-bottom: 12px;
    cursor: pointer;
    display: block;
    &:hover {
      background-color: $secondary;
    }
    .image {
      display: inline-block;
      width: 75px;
      height: 75px;
      background-image: url("https://scale.lwcdn.nl/imageScaled/?site=sportbedrijf&file=1626076330_8481.jpg&w=720&h=405&cropped=1&orientation=undefined");
      background-size: cover;
      background-repeat: no-repeat;
      background-position: center center;
    }
    h4 {
      font-weight: light;
      color: white;
      font-size: 20px;
      font-family: "Open Sans Condensed";
    }
  }
}
</style>