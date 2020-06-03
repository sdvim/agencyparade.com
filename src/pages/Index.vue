<template>
  <Layout>
    <section class="flex flex-column flex-j-center min-height-vh">
      <div class="content-container">
        <h1 class="gradient-text mb2">Create digital experiences your customers will love</h1>
        <p class="light-text width-6-col">Parade is a design team helping businesses elevate their web and mobile experiences.</p>
      </div>
    </section>
    <hr>
    <section class="content-container flex pt6 pb5">
      <div class="width-6-col flex flex-1">
        <g-image alt="Design planning" src="~/assets/images/design-flow.svg" width="488" height="265" blur="5" />
      </div>
      <div class="width-6-col flex-1">
        <h2 class="mb3">Design an experience</h2>
        <p>Your customer’s needs are unique, so how they interact with you via web and mobile must be unique as well. We develop and redesign platforms with one goal in mind: creating user-friendly, optimized, and distinctive digital experiences for your customers.</p>
        <ul class="small-text">
          <li>Align on vision and project goals</li>
          <li>Design and validate concepts</li>
          <li>Deliver high fidelity assets ready for development</li>
        </ul>
        <button class="btn--gradient">Ask about this</button>
      </div>
    </section>
    <section class="bg-content">
      <div class="content-container flex pt6 pb5">
        <div class="width-6-col flex-1">
          <h2 class="mb3">Evaluate your<br>product or website</h2>
          <p>We conduct an in-depth audit to identify what exactly your customers are looking for and pinpoint the spots where user experience can be improved.</p>
          <ul class="small-text">
            <li>Quickly uncover usability issues</li>
            <li>Validate designs with real users</li>
            <li>Maximize efficiency for your customers</li>
          </ul>
          <button class="btn--gradient">Ask about this</button>
        </div>
        <div class="width-6-col flex flex-1">
          <g-image alt="Product evaluation" src="~/assets/images/evaluate-flow.svg" width="488" height="288" blur="5" style="margin-left: auto;" />
        </div>
      </div>
    </section>
    <blockquote class="content-container text-center pt9 pb9">
      <p class="large-text">“Parade functioned as part of our team, helping to crystalize our vision and delivering incredible results in record time”</p>
      <footer class="small-text">– Brian, Product Manger at Telnyx</footer>
    </blockquote>
    <hr>
    <section class="content-container pt6">
      <h4>RECENT WORK</h4>
      <div class="flex flex-between pt5 pb5">
        <div class="width-5-col" style="align-self: center;">
          <h3>Helping Pressed validate a cross platform, on-demand laundry service</h3>
          <p class="small-text">UX & UI for an MVP for Pressed</p>
          <button class="btn--gradient">Approach</button>
        </div>
        <div class="width-5-col ratio-square bg-moody-blue">
        </div>
      </div>
    </section>
    <section class="bg-content">
      <div class="content-container flex flex-between pt5 pb5">
        <div class="width-5-col" style="align-self: center;">
          <h3>Increasing conversion for a growing networking company</h3>
          <p class="small-text">UX & Information Architecture for Telnyx</p>
          <button class="btn--gradient">Approach</button>
        </div>
        <div class="width-5-col ratio-square bg-celeste">
        </div>
      </div>
    </section>
    <section class="bg-dark">
      <div class="content-container pt6 pb6 white-text">
        <h4>RECENT WORK</h4>
        <p class="width-6-col">Our team has experience working with startups and large enterprises across various industries.</p>
        <div class="flex flex-wrap flex-between width-8-col">
          <div class="width-2-col text-center mt4" v-for="(label, key) in industries" :key="key">
            <img :alt="label" :src="`/icons/${key}.svg`" width="48" height="48" />
            <p class="small-text white-text">{{ label }}</p>
          </div>
        </div>
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
  },
  data() {
    return {
      industries: {
        b2b: 'B2B',
        saas: 'SaaS',
        marketplace: 'Marketplace',
        tourism: 'Tourism',
        transportation: 'Transportation',
        finance: 'Finance',
        enterprise: 'Enterprise',
        government: 'Government',
      }
    };
  }
}
</script>