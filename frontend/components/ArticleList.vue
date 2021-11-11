<template>
  <div class="article-block-items d-flex row" v-editable="blok">
      <div :class="blok.per_row" v-for="item in articles.slice(0, 8)" :key="item.id">
        <NuxtLink :to="item.full_slug" class="item" >
          <img :src="item.content.image" alt="Sportbedrijf image" />
          <h4>{{ item.name }}</h4>
        </NuxtLink>
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
      story: { stories: {} },
      articles: [],
    };
  },
  mounted() {
    console.log(this.story.content);
  },

  asyncData(context) {
    // let data = {
    //   version: "draft",
    //   starts_with: "news",
    //   token: process.env.STORYBLOK_TOKEN,
    //   excluding_slugs: "news/,news/zwemmen/,news/zwemmen/diploma/",
    // };
    // let config = {
    //   method: "get",
    //   url: `https://api.storyblok.com/v2/cdn/stories/`,
    //   headers: {
    //     "Content-Type": "application/json",
    //     Accept: "application/json",
    //   },
    //   params: data,
    // };
    // axios(config).then((response) => {
    //   return response.data;
    // });
  },

  created() {
    console.log(this.blok)
    var data = {
      version: "draft",
      starts_with: this.blok.article_folder,
      token: process.env.STORYBLOK_TOKEN,
      excluding_slugs: "news/,news/zwemmen/,news/zwemmen/diploma/,news/schaatsen/",
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
      console.log(response);
      this.articles = response.data.stories;
    });
  },
};
</script>

<style lang="scss" scoped>
.article-block-items {
  margin-right: -6px;
  margin-left: -6px;
  .col-6,
  .col-4,
  .col-3,
  .col-2 {
    padding-left: 6px;
    padding-right: 6px;
  }
  .col-12 {
    padding-left: 6px;
    padding-right: 6px;
  }

  .item {
    display: block;
    position: relative;
    height: 0;
    padding-bottom: 56.25%;
    overflow: hidden;
    margin-bottom: 12px;
    cursor: pointer;
    &:hover {
      img {
        transform: scale(1.05);
      }
    }
    &:before {
      content: "";
      position: absolute;
      bottom: 0;
      left: 0;
      width: 100%;
      height: 50%;
      background: linear-gradient(
        to bottom,
        rgba(0, 0, 0, 0) 0,
        rgba(0, 0, 0, 0.61) 53%,
        rgba(0, 0, 0, 0.61) 100%
      );
      z-index: 2;
    }
    img {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      transition: transform 0.4s;
      object-fit: cover;
    }
    h4 {
      position: absolute;
      bottom: 0.25rem;
      left: 0.75rem;
      z-index: 5;
      color: white;
      font-size: 20px;
      line-height: 1.2;
      text-transform: uppercase;
    }
  }
  .col-2 {
    h4 {
      bottom: 0.125rem;
      left: 0.75rem;
      max-height: 3rem;
      overflow: hidden;
      font-size: 16px;
    }
  }
}
</style>