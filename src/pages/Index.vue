<template>
  <Layout>
    <section class="flex flex-column pt6 pb5 flex-j-center">
      <div class="content-container pvhh">
        <h1 class="gradient-text mb2">Create digital experiences your customers will love</h1>
        <p class="color-grey width-6-col">Parade is a design team helping businesses elevate their web and mobile experiences.</p>
      </div>
    </section>
    <hr>
    <section class="content-container flex pt6 pb5 mbp-flex-column">
      <div class="width-6-col flex flex-1 flex-j-start pr2 mbp-mb4">
        <g-image alt="Design planning" src="~/assets/images/design-flow.svg" width="488" height="265" blur="5" />
      </div>
      <div class="width-6-col flex-1">
        <h2 class="mb3 mbp-mb2">Design an experience</h2>
        <p>Your customer’s needs are unique, so how they interact with you via web and mobile must be unique as well. We develop and redesign platforms with one goal in mind: creating user-friendly, optimized, and distinctive digital experiences for your customers.</p>
        <ul class="fs-small mt2 mb2 color-grey">
          <li>Align on vision and project goals</li>
          <li>Design and validate concepts</li>
          <li>Deliver high-fidelity assets ready for development</li>
        </ul>
        <button class="btn--gradient" @click="scrollToForm('design')">Ask about this</button>
      </div>
    </section>
    <section class="bg-offwhite">
      <div class="content-container flex pt6 pb5 mbp-flex-column">
        <div class="width-6-col flex-1">
          <h2 class="mb3 mbp-mb2">Evaluate your<br>product or website</h2>
          <p>We conduct an in-depth audit to identify what exactly your customers are looking for and pinpoint the spots where the user experience can be improved.</p>
          <ul class="fs-small mt2 mb2 color-grey">
            <li>Quickly uncover usability issues</li>
            <li>Validate designs with real users</li>
            <li>Maximize efficiency for your customers</li>
          </ul>
          <button class="btn--gradient" @click="scrollToForm('evaluate')">Ask about this</button>
        </div>
        <div class="width-6-col flex flex-1 flex-j-end pl2 mbp-mb4 mbp-flex-o-1">
          <g-image alt="Product evaluation" src="~/assets/images/evaluate-flow.svg" width="488" height="288" blur="5" />
        </div>
      </div>
    </section>
    <blockquote class="content-container text-center pt9 pb9">
      <p class="fs-large mb1">“We gave Parade an incredibly complex project with a broad range of industry-specific requirements, and they were able to build us an excellent mock-up that was used to build a useful product.”</p>
      <footer class="fs-small color-grey">– Product Manager at Telnyx</footer>
    </blockquote>
    <hr>
    <section class="content-container pt6">
      <h4 class="mb2 width-10-col mla mra">RECENT WORK</h4>
      <div class="flex flex-between pt3 pb3 mbp-flex-column">
        <div class="width-7-col flex flex-center mbp-width-full">
          <div class="width-5-col mbp-width-full">
            <h3>Helping Pressed validate a cross platform, on-demand laundry service</h3>
            <p class="fs-small color-grey mt1 mb2">UX & UI for an MVP for Pressed</p>
            <g-link class="btn btn--gradient" to="/approach">Our Approach</g-link>
          </div>
        </div>
        <div class="width-5-col ratio-square bg-moody-blue mbp-flex-o-1 mbp-width-full mbp-mb2">
          <g-image class="pl4 pt4 pb4" alt="Pressed UI mockups" src="~/assets/images/work-pressed.png" blur="5" />
        </div>
      </div>
    </section>
    <section class="bg-offwhite">
      <div class="content-container flex flex-between pt3 pb3 mbp-flex-column">
        <div class="width-7-col flex flex-center mbp-width-full">
          <div class="width-5-col mbp-width-full">
            <h3>Increasing conversion for a growing networking company</h3>
            <p class="fs-small color-grey mt1 mb2">UX & Information Architecture for Telnyx</p>
            <g-link class="btn btn--gradient" to="/approach">Our Approach</g-link>
          </div>
        </div>
        <div class="width-5-col ratio-square bg-celeste mbp-flex-o-1 mbp-width-full mbp-mb2">
          <g-image class="pl4 pt4 pb2" alt="Telnyx UI mockup" src="~/assets/images/work-telnyx.png" blur="5" />
        </div>
      </div>
    </section>
    <section class="bg-darkgrey">
      <div class="content-container pv6 mbp-pv4 color-white flex flex-j-center">
        <div class="width-10-col">
          <h4 class="mb2">INDUSTRIES WE’VE WORKED IN</h4>
          <p class="width-6-col">Our team has experience working with startups and large enterprises across various industries.</p>
          <div class="flex flex-wrap flex-between width-8-col">
            <div class="width-2-col text-center mt4 mbp-width-half" v-for="(label, key) in industries" :key="key">
              <img :alt="label" :src="`/icons/${key}.svg`" width="48" height="48" />
              <p class="fs-small color-white mt1">{{ label }}</p>
            </div>
          </div>
        </div>
      </div>
    </section>
  </Layout>
</template>

<script>
export default {
  metaInfo: {
    title: 'Home'
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
  },
  methods: {
    scrollToForm(index) {
      const top = document.querySelector('.contact-form').offsetTop;
      const behavior = 'smooth';
      this.$root.$emit('selectSubject', index);
      window.scroll({ top, behavior });
    }
  }
}
</script>
