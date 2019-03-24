<template>
  <Layout>
    <h1 class="tag-title text-center space-bottom">
      Tags
    </h1>

    <div >
        	<g-link class="post-tags__link" v-for="tag in tags" :key="tag.node.id" :to="tag.node.path">
   			<span>#</span>{{ tag.node.title }}&nbsp;({{ tag.node.belongsTo.edges.length }})
   		</g-link>
      
    </div>
  </Layout>
</template>

<page-query>
query {
  allTag (sortBy:"id", order:ASC){
    totalCount
    edges {
      node {
        id
        path
        title
        belongsTo {
          edges {
            node {
              __typename
            }
          }
        }
      }
    }
  }
}

</page-query>

<script>
import Author from '~/components/Author.vue'
import PostCard from '~/components/PostCard.vue'

export default {
  components: {
    Author,
    PostCard
  },
  metaInfo: {
    title: 'Hello, world!'
  },
  computed:{
    tags(){
      const tags = this.$page.allTag.edges
      return tags.sort(compareByNumberOfPosts)
    }
  }

}

function compareByNumberOfPosts(tagA, tagB) {
  if (tagA.node.belongsTo.edges.length < tagB.node.belongsTo.edges.length)
     return 1;
  if (tagB.node.belongsTo.edges.length < tagA.node.belongsTo.edges.length)
     return -1;
  // a doit être égal à b
  return 0;
}
</script>

<style lang="scss">

</style>

