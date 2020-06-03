<template>
  <Layout>
    <section class="hero min-height-vh">
      <div class="content-center">
        <h1 class="gradient-text">Create digital experiences your customers will love</h1>
        <p class="light-text width-6-col">Parade is a design team helping businesses elevate their web and mobile experiences.</p>
      </div>
    </section>
    <section class="content-center flex pt6">
      <div class="width-6-col flex flex-1">
        <g-image alt="Design planning" src="~/assets/images/design-flow.svg" width="488" height="265" blur="5" />
      </div>
      <div class="width-6-col flex-1">
        <h2>Design an experience</h2>
        <p>Your customer’s needs are unique, so how they interact with you via web and mobile must be unique as well. We develop and redesign platforms with one goal in mind: creating user-friendly, optimized, and distinctive digital experiences for your customers</p>
        <ul class="small-text">
          <li>Align on vision and project goals</li>
          <li>Design and validate concepts</li>
          <li>Deliver high fidelity assets ready for development</li>
        </ul>
        <button class="btn--gradient">Ask about this</button>
      </div>
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
  border-bottom: 2rem solid;
  h1 {
    margin-bottom: 2rem;
  }
}
h2 {
  margin-bottom: 2.666rem;
}
</style>