<template>
  <div class="rubric-list" v-editable="blok">
    <h5 class="">Rubrieken</h5>
    <ul class="m-0 p-0" v-for="item in rubricList" :key="item.id">
      <li v-if="item.content.component == 'page'">
      <NuxtLink :to="'/rubrics/'+ item.slug" class="py-3 px-3 mb-2" style="display: block" >
        {{ item.name }}
      </NuxtLink>
      </li>
    </ul>
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
      rubricList: []
    };
  },
  created() {
    var data = {
      version: "draft",
      starts_with: "rubrics",
      token: process.env.STORYBLOK_TOKEN,
      excluding_slugs: "rubrics/",
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
      this.rubricList = response.data.stories
    });
  },
};
</script>

<style lang="scss" scoped>
.rubric-list {
  h5 {
  }
  ul {
    list-style-type: none;
    li {
      font-family: $headingstack;
      color: white;
      font-size: 24px;
      background-color: $primary;
      line-height: 1;
      cursor: pointer;
      
      a{
        color: white;
        text-decoration: none;
        transition: color 0.4s;
      }
      &:hover {
        a{
          color: rgba(255, 255, 255, 0.6);
        }
        
      }
    }
  }
}
</style>