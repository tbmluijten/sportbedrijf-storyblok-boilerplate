	<template>
  <b-breadcrumb class='mb-2' :items="crumbs"/>
</template>

<script>
export default ({
  computed: {
    crumbs: function() {
      let pathArray = this.$route.path.split("/")
      pathArray.shift()
      let object = '{ "path": "", "to": "/", "text": "Home" }'
      let breadcrumbs = []
      breadcrumbs.push(object)
      breadcrumbs = pathArray.reduce((breadcrumbArray, path, idx) => {
        breadcrumbArray.push({
          path: path,
          to: breadcrumbArray[idx - 1] ?  breadcrumbArray[idx - 1].to + "/" + path : "/" + path,
          text: path,
        });
        return breadcrumbArray;
      }, [])
      
      breadcrumbs.unshift(JSON.parse(object))

      return breadcrumbs;
    }
  }
})
</script>

<style lang="scss">
  .breadcrumb {
    padding: 0;
    margin: 0;
    background-color: rgba(0,0,0,0);
    .breadcrumb-item + .breadcrumb-item::before{
      content: '»'
    }
    .breadcrumb-item{
      text-transform: capitalize;
    }
  }
</style>