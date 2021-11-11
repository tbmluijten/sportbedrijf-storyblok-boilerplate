<template>
  <div class="container" v-editable="blok">
    <div class="holder-articles mt-5 p-4">
      <Breadcrumb />
      <h1 class="mb-2 mt-0">{{blok.title}}</h1>
      <div class="row article-content">
        <div class="col-12 col-lg-8">
          <p class="bold">{{blok.subtitle}}</p>
          {{blok.body}}
          <div class="socials" v-if="blok.socials">
            <div class="social-title">Artikel delen</div>
            <div class="holder-socials">
              <ShareNetwork network="facebook" title="Testtitle" description="testdescription" url="https://news.vuejs.org/issues/180" class="item"><div class="icon"></div></ShareNetwork>
              <ShareNetwork network="facebook" title="Testtitle" description="testdescription" url="https://news.vuejs.org/issues/180" class="item"><div class="icon"></div></ShareNetwork>
              <ShareNetwork network="facebook" title="Testtitle" description="testdescription" url="https://news.vuejs.org/issues/180" class="item"><div class="icon"></div></ShareNetwork>
              <ShareNetwork network="facebook" title="Testtitle" description="testdescription" url="https://news.vuejs.org/issues/180" class="item"><div class="icon"></div></ShareNetwork>
            </div>
          </div>
        </div>
        <div class="col-12 col-lg-4">
          <component
            v-for="blok in blok.Sidebar"
            :key="blok._uid"
            :blok="blok"
            :is="blok.component" 
          />
        </div>
      </div>
    </div>
  </div>
</template>

 
<script>
export default {
  data () {
    return {
      story: { stories: {} }
    }
  },
  props: {
    blok: {
      type: Object,
      required: true
    }
  },
  mounted () {
    console.log(this.story.content)
  },

  asyncData (context) {
    const articleSlug = context.route.params.slug
    return context.app.$storyapi.get(`cdn/stories/`, {
      version: 'draft',
      starts_with: 'posts',
      with_tag: 'zwemmen',
      by_slugs: `posts/${articleSlug}`
    }).then((res) => {
      console.log(res.data)
      return res.data
    }).catch((res) => {
      if (!res.response) {
        console.error(res)
        context.error({ statusCode: 404, message: 'Failed to receive content form api' })
      } else {
        console.error(res.response.data)
        context.error({ statusCode: res.response.status, message: res.response.data })
      }
    })
    
  }
}
</script>

<style lang="scss">
  .holder-articles{
    background-color: white;
    h1{
        font-size: 48px;
    }
    p.bold{
      font-weight: bold;
    }
    .article-content{
      h2{
        color: #009cda;
        font-size: 18px;
        font-weight: bold;
        font-family: 'Open Sans';
      }
      ol, ul{
        padding-left: 1.75rem;
        li{
          padding-left: 0.50rem;
        }
      }
      a{
        color: #2c6596;
        font-weight: bold;
      }
    }
    .socials{
      width: 100%;
      margin-top: 48px;
      .social-title{
          font-family: "Trade Gothic LT Std", sans-serif;
          font-size: 24px;
        }
      .holder-socials{
        display: flex;
        width:100%;
        
        .item{
          width: 100%;
          padding: 12px 24px;
          min-height: 80px;
          background-color: red;
          &:nth-child(2n + 2){
            background-color: orange;

          }
        }
      }
    }
  }
</style>