<template>
  <div class="article-block-menu" v-editable="blok">
    <!-- <pre>{{blok}}</pre> -->
    <div class="container">
      <div class="holder-submenu-items row m-0 mb-2" :class="blok.color_scheme">
        <div
          class="article-item p-4 col-6 col-lg-3"
          v-for="item in blok.menu_item"
          :key="item._uid"
        >
          <h3>{{ item.title }}</h3>
          <div class="search" v-if="item.searchblock">
            <input type="text" :placeholder="item.search_placeholder" />
            <div class="submit" @click="setSearch">
              <img src="@/assets/img/search-article-menu.png" alt="" />
            </div>
          </div>
          <NuxtLink class="note" :to="item.link.cached_url" v-else
            >{{ item.link_text }}
            <img src="@/assets/img/icon_quicklink_arrow@2x.png" alt=""
          /></NuxtLink>
        </div>
      </div>
    </div>
  </div>
</template>
 
<script>
export default {
  props: {
    blok: {
      type: Object,
      required: true,
    },
  },

  methods: {
    setSearch() {
      console.log("setting search");
    },
  },
};
</script>

<style lang="scss" scoped>
.article-block-menu {
  margin-bottom: 48px;
  .article-item {
    position: relative;
    top: 0;
    color: white;

    height: 180px;
    cursor: pointer;
    transition: top 0.4s;
    h3 {
      text-transform: uppercase;
      line-height: 1;
    }
    .search {
      display: flex;
      background-color: white;
      padding: 8px 8px;
      width: 100%;
      input {
        border: none;
        // width: 80%;
        padding: 0 16px;
        line-height: 1;
        width: 100%;
        outline: none;
      }
      img {
        width: 24px;
        height: 24px;
      }
    }
    .note {
      opacity: 0;
      transition: opacity 0.4s;
      position: absolute;
      bottom: 0.75rem;
      right: 1.5rem;
      color: white;
      text-decoration: none;
      img {
        width: 16px;
        height: 16px;
      }
    }
    &:hover {
      top: -24px;
      .note {
        opacity: 1;
      }
    }
  }

  .holder-submenu-items {
    &.orange-theme {
      .article-item {
        background-color: #f49244;
        &:nth-child(2n + 2) {
          background-color: #f06e05;
        }
      }
    }
    &.green-theme {
      .article-item {
        background-color: #49b29c;
        &:nth-child(2n + 2) {
          background-color: #009677;
        }
      }
    }
    &.blue-theme {
      .article-item {
        background-color: #026596;
        &:nth-child(2n + 2) {
          background-color: #152d51;
        }
      }
    }
  }
}
</style>
