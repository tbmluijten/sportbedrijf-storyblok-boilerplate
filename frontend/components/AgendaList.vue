<template>
  <div class="agenda-list" v-editable="blok">
    <h5 class="mb-3 pb-3">Agenda</h5>
    <ul class="m-0 p-0">
      <li class=" pb-3 mb-3" v-for="item in agenda.slice(0, 4)" :key="item.id">
        <NuxtLink :to="item.full_slug" class="d-flex align-items-start">
        <div class="date py-2">
          <div class="day">{{ item.content.date | moment("DD") }}</div>
          <div class="month">
            {{ item.content.date | moment("MMM") }}
          </div>
        </div>
        <div class="label py-1">{{ item.content.title }}</div>
        <div class="label"></div>
        </NuxtLink>
      </li>
    </ul>
    <!-- <NuxtLink class="agenda-more" to="/">Meer nieuws >></NuxtLink> -->
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
      agenda: [],
    };
  },
  created() {
    console.log(this.$route.params.pathMatch)
    var data = {
      version: "draft",
      starts_with: "agenda/",
      token: process.env.STORYBLOK_TOKEN,
      excluding_slugs: "agenda/",
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
      this.agenda = response.data.stories;
    });
  },
};
</script>

<style lang="scss" scoped>
.agenda-list {
  h5 {
    border-bottom: solid 1px rgba(0, 0, 0, 0.2);
  }
  ul {
    list-style-type: none;
    li {
      border-bottom: solid 1px rgba(0, 0, 0, 0.2);
      cursor: pointer;
      a{
          text-decoration: none;
          display: block;
      }
      &:hover {
        .date {
          background-color: $secondary;
        }
      }
      .date {
        width: 56px;
        height: 56px;
        color: white;
        background-color: $primary;
        line-height: 1;
        text-align: center;
        margin-right: 12px;
        &:hover {
          background-color: $secondary;
        }
        .day {
          font-size: 24px;
        }
        .month {
          font-size: 12px;
          opacity: 0.6;
        }
      }
      .label {
        font-family: $headingstack;
      }
    }
  }
  .agenda-more {
    color: black;
    text-align: right;
    display: block;
  }
}
</style>