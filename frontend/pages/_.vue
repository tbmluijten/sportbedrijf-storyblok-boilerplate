<template>
  <section>
    <!-- <pre>{{story}}</pre> -->
    <component
      v-if="story.content.component"
      :key="story.content._uid"
      :blok="story.content"
      :is="story.content.component" />
      
  </section>
  
</template>

 
<script>
export default {
  data () {
    return {
      story: { content: {} }
    }
  },
  mounted () {
    this.$storybridge(() => {
      // Create Story Book Instance for live edit
      const storyblokInstance = new StoryblokBridge()
 
      // Use the input event for instant update of content
      storyblokInstance.on('input', (event) => {
        console.log(this.story.content)
        if (event.story.id === this.story.id) {
          this.story.content = event.story.content
        }
      })
 
      // Use the bridge to listen the events
      storyblokInstance.on(['published', 'change'], (event) => {
        this.$nuxt.$router.go({
          path: this.$nuxt.$router.currentRoute,
          force: true,
        })
      })
    })
  },
  asyncData (context) {
    // Get DEV or PROD version (untested)
    // const version = context.query._storyblok || context.isDev ? 'draft' : 'published'

    // Use full slug path from Storyblok CMS pages
    const fullSlug = (context.route.path == '/' || context.route.path == '') ? 'home' : context.route.path
    console.log(fullSlug, '<--- COMPLETE SLUG')
    return context.app.$storyapi.get(`cdn/stories/${fullSlug}`, {
      version: 'draft' // Set DEV of PROD version (untested)
    }).then((res) => {
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