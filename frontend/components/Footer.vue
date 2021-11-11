<template>
  <div class="footer">
    <div class="container my-5">
      <div class="row">
        <div class="col-6 col-lg-3">
          <h4 class="mb-3">Accomodaties</h4>
          <ul class="m-0 p-0 mb-3">
            <li><NuxtLink to="/">Ireen Wust Ijsbaan</NuxtLink></li>
            <li><NuxtLink to="/">Ireen Wust Ijsbaan</NuxtLink></li>
            <li><NuxtLink to="/">Ireen Wust Ijsbaan</NuxtLink></li>
            <li><NuxtLink to="/">Ireen Wust Ijsbaan</NuxtLink></li>
            <li><NuxtLink to="/">Ireen Wust Ijsbaan</NuxtLink></li>
          </ul>
          <NuxtLink class="more" to="/">Meer bekijken..</NuxtLink>
        </div>
        <div class="col-6 col-lg-3">
          <h4 class="mb-3">Accomodaties</h4>
          <ul class="m-0 p-0 mb-3">
            <li><NuxtLink to="/">Ireen Wust Ijsbaan</NuxtLink></li>
            <li><NuxtLink to="/">Ireen Wust Ijsbaan</NuxtLink></li>
            <li><NuxtLink to="/">Ireen Wust Ijsbaan</NuxtLink></li>
            <li><NuxtLink to="/">Ireen Wust Ijsbaan</NuxtLink></li>
            <li><NuxtLink to="/">Ireen Wust Ijsbaan</NuxtLink></li>
          </ul>
          <NuxtLink class="more" to="/">Meer bekijken..</NuxtLink>
        </div>
        <div class="col-6 col-lg-3">
          <h4 class="mb-3">Accomodaties</h4>
          <ul class="m-0 p-0 mb-3">
            <li><NuxtLink to="/">Ireen Wust Ijsbaan</NuxtLink></li>
            <li><NuxtLink to="/">Ireen Wust Ijsbaan</NuxtLink></li>
            <li><NuxtLink to="/">Ireen Wust Ijsbaan</NuxtLink></li>
            <li><NuxtLink to="/">Ireen Wust Ijsbaan</NuxtLink></li>
            <li><NuxtLink to="/">Ireen Wust Ijsbaan</NuxtLink></li>
          </ul>
          <NuxtLink class="more" to="/">Meer bekijken..</NuxtLink>
        </div>
        <div class="col-6 col-lg-3">
          <h4 class="mb-3">Accomodaties</h4>
          <ul class="m-0 p-0 mb-3">
            <li><NuxtLink to="/">Ireen Wust Ijsbaan</NuxtLink></li>
            <li><NuxtLink to="/">Ireen Wust Ijsbaan</NuxtLink></li>
            <li><NuxtLink to="/">Ireen Wust Ijsbaan</NuxtLink></li>
            <li><NuxtLink to="/">Ireen Wust Ijsbaan</NuxtLink></li>
            <li><NuxtLink to="/">Ireen Wust Ijsbaan</NuxtLink></li>
          </ul>
          <NuxtLink class="more" to="/">Meer bekijken..</NuxtLink>
        </div>
      </div>
    </div>
    <div class="bottom-row">
      <img class="footer-logo" src="@/assets/img/footerlogo.svg" />
      <div class="container">
        <div class="row">
          <div class="col-12 col-lg-4">
            <div class="title mb-3">Sport in tilburg app</div>
            <div class="holder-store-images d-flex">
              <a class="mr-2" href="#"
                ><img
                  src="@/assets/img/badge-appstore@2x.png"
                  alt="apple-store-logo"
              /></a>
              <a href="#"
                ><img
                  src="@/assets/img/badge-googleplay@2x.png"
                  alt="apple-store-logo"
              /></a>
            </div>
          </div>
          <div class="col-12 col-lg-8">
            <ul class="d-flex">
              <li class="mx-2"><NuxtLink to="/">Proclaimer</NuxtLink></li>
              <li class="mx-2"><NuxtLink to="/">Proclaimer</NuxtLink></li>
              <li class="mx-2"><NuxtLink to="/">Proclaimer</NuxtLink></li>
              <li class="mx-2"><NuxtLink to="/">Proclaimer</NuxtLink></li>
            </ul>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {};
</script>

<style lang="scss" scoped>
.footer {
  background-color: white;
  padding-top: 24px;
  .container {
    .row {
      font-family: $headingstack;
      h4 {
        line-height: 1;
        font-size: 18px;
        color: $primary;
        text-transform: uppercase;
      }
      ul {
        list-style-type: none;
        li a {
          font-size: 18px;
          color: #3e3e3e;
        }
      }
      .more {
        color: $secondary;
        font-size: 14px;
      }
    }
  }
  .bottom-row {
    background-color: $primary;
    position: relative;
    .footer-logo {
      position: absolute;
      right: 1.5rem;
      top: -32px;
    }
    .container {
      padding: 48px 16px;
      .row {
        .title {
          font-size: 15px;
          color: white;
          line-height: 1;
          font-weight: bold;
          text-transform: uppercase;
          font-family: $headingstack;
        }
        .holder-store-images {
          img {
            height: 40px;
          }
        }
      }
      ul {
        list-style-type: none;
        li a {
          color: white;
          font-family: $headingstack;
        }
      }
    }
  }
}
</style>