<template>
  <div class="container">
    <div class="navigation">
      <div class="holder-navigation d-flex pr-3">
        <img src="@/assets/img/topbar_logo@2x.png" class="logo" />
        <ul class="holder-menu-items d-flex p-0 m-0">
          <li class="px-3"><NuxtLink to="/">Home</NuxtLink></li>
          <li class="px-3"><NuxtLink to="/zwemmen">Zwemmen</NuxtLink></li>
          <li class="px-3"><NuxtLink to="/schaatsen">Schaatsen</NuxtLink></li>
          <li class="px-3"><NuxtLink to="/huren">Huren</NuxtLink></li>
          <li class="px-3">
            <NuxtLink to="/programmas">Programma's</NuxtLink>
          </li>
          <li class="px-3"><NuxtLink to="/contact">Contact</NuxtLink></li>
        </ul>
        <div class="holder-misc-links d-none d-lg-flex ml-auto">
          <a class="py-2 px-3" href="/">webshop</a>
          <a class="p-2" href="/"
            ><img src="@/assets/img/social/facebook/facebook64x64_white.png"
          /></a>
          <a class="p-2" href="/"
            ><img src="@/assets/img/social/linkedin/linkedin64x64_white.png"
          /></a>
          <a class="p-2" href="/"
            ><img src="@/assets/img/social/instagram/instagram64x64_white.png"
          /></a>
        </div>
        <div
          class="open-subnavigation d-block d-lg-none"
          @click="openSubnavigation()"
        ></div>
        <div class="holder-search d-none">
          <input type="text" placeholder="Zoeken.." />
          <div class="button-search"></div>
        </div>
      </div>
      <transition name="fade">
        <div
          class="
            holder-subnavigation
            d-flex d-lg-none
            px-3
            py-2
            justify-content-end
          "
          v-if="subNavigation"
        >
          <a class="py-2 px-3" href="/">webshop</a>
          <a class="p-2" href="/"
            ><img src="@/assets/img/social/facebook/facebook64x64_white.png"
          /></a>
          <a class="p-2" href="/"
            ><img src="@/assets/img/social/linkedin/linkedin64x64_white.png"
          /></a>
          <a class="p-2" href="/"
            ><img src="@/assets/img/social/instagram/instagram64x64_white.png"
          /></a>
        </div>
      </transition>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      subNavigation: false,
    };
  },
  methods: {
    openSubnavigation() {
      this.subNavigation = !this.subNavigation;
    },
  },
};
</script>

<style lang="scss">
.navigation {
  background-color: white;
  position: relative;
  z-index: 100;
  .holder-navigation {
    position: relative;
    z-index: 2;
    align-items: center;
    box-shadow: 0 6px 12px 0 rgba(29, 29, 27, 0.12),
      0 1px 0 0 rgba(29, 29, 27, 0.05);
    .logo {
      height: 80px;
    }
    ul {
      list-style-type: none;
      li {
        a {
          font-family: $headingstack;
          font-size: 18px;
          text-transform: uppercase;
          color: $primary;
        }
        &:hover a {
          color: $secondary;
        }
      }
    }
    .open-subnavigation {
      width: 40px;
      height: 40px;
      background-color: $primary;
      cursor: pointer;
    }
  }
  .holder-misc-links,
  .holder-subnavigation {
    a {
      display: inline-block;
      background-color: $primary;
      color: white;
      text-align: center;
      font-weight: bold;
      text-transform: uppercase;
      margin-right: 4px;
      img {
        height: 24px;
      }
      &:last-child {
        margin-right: 0;
      }
    }
  }
  .holder-subnavigation {
    background-color: white;
    z-index: 1;
  }
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}
</style>
