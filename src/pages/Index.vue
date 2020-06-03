<template>
  <Layout>
    <section class="hero content-center min-height-vh">
      <h1 class="gradient-text">Create digital experiences your customers will love</h1>
      <p class="light-text width-6-col">Parade is a design team helping businesses elevate their web and mobile experiences.</p>
    </section>
  </Layout>
</template>

<page-query>
query {
  posts: allPost(filter: { published: { eq: true }}) {
    edges {
      node {
        id
        title
        date (format: "D. MMMM YYYY")
        timeToRead
        description
        cover_image (width: 770, height: 380, blur: 10)
        path
        tags {
          id
          title
          path
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
  }
}
</script>

<style lang="scss">
.hero {
  display: flex;
  flex-direction: column;
  justify-content: center;
  h1 {
    margin-bottom: 2rem;
  }
}
</style>