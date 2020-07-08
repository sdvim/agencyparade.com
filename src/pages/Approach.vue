<template>
  <Layout>
    <section class="flex flex-column flex-j-center min-height-vh pv6 mbp-pv4">
      <div class="content-container flex flex-between flex-a-center mbp-flex-column pvhh">
        <div class="width-6-col">
          <h1 class="mb2">Approach</h1>
          <p class="color-grey">We communicate insight early and often, functioning as an embedded part of your team to deliver solutions built on a shared vision.</p>
        </div>
        <div class="width-5-col ml2 mbp-width-full mbp-ml0 mbp-mt4">
          <g-image src="~/assets/images/approach.svg" />
        </div>
      </div>
    </section>
    <section class="bg-offwhite pv6 mbp-pv4">
      <div class="content-container flex flex-j-end">
        <div class="width-8-col">
          <h4>PROCESS</h4>
          <div class="flex flex-between pt2 pb4 mbp-flex-column" :class="index !== Object.keys(processes).length - 1 ? 'bb1' : ''" v-for="(text, title, index) in processes" :key="title">
            <h3 class="flex-1 width-3-col text-capitalize mbp-mb1">{{ title }}</h3>
            <p class="flex-1 fs18">{{ text }}</p>
          </div>
        </div>
      </div>
    </section>
    <section class="bg-darkgrey pv6 mbp-pv4">
      <div class="content-container flex flex-j-center">
        <div class="width-10-col">
          <h4 class="mb2">CAPABILITIES</h4>
          <div class="flex flex-wrap mbp-flex-column">
            <div class="width-3-col tbp-width-half mbp-width-full tbp-mb3" v-for="(list, title) in capabilities" :key="title">
              <h3 class="color-grey mb2">{{ title }}</h3>
              <ul class="fs18 mb0 color-white">
                <li v-for="item in list" :key="item">{{ item }}</li>
              </ul>
            </div>
          </div>
        </div>
      </div>
    </section>
    <section class="pt9 pb9">
      <div class="content-container flex flex-j-center ">
        <div class="width-10-col flex flex-j-between flex-a-center tbp-flex-column">
          <div class="width-5-col mbp-width-full tbp-mb3">
            <g-image src="~/assets/images/development.svg" />
          </div>
          <p class="fs-large width-5-col ml1c mbp-width-full tbp-ml0 tbp-text-center">Execute confidently with development-ready designs your engineering team needs</p>
        </div>
      </div>
    </section>
    <hr>
  </Layout>
</template>

<script>
export default {
  metaInfo: {
    title: 'Our Approach'
  },
  data() {
    return {
      processes: {
        discovery: 'Each project begins by learning more about your business and customers. We gather requirements, pain points, and align on goals for success.',
        audit: 'Our evaluation includes an in-depth review of your website or product\'s content, navigation, interface, and overall user experience.',
        wireframe: 'Once we are aligned with your customers goals, we will create wireframes. This is done to layout the content and functionality of each page.',
        test: 'Usability testing ensures that functionality and layout are aligned to customer needs.',
        style: 'We use you brand\'s identity is used as inspiration for color themes, font, icons, and hi-fidelity designs. Down’t worry if you haven’t figured it out yet, we can help with that too.',
        deliver: 'We\'ll leave you with high fidelity mockups and an interactive prototype ready for handoff to engineers.',
      },
      capabilities: {
        Research: [
          'Usability testing',
          'User Interviews',
          'Heuristic analysis',
          'A/B testing',
        ],
        UX: [
          'Personas',
          'User flows',
          'Wireframes',
          'Information architecture',
        ],
        UI: [
          'High-fidelity mockups',
          'Interactive prototypes',
          'Visual direction',
          'Design systems',
        ],
      },
    };
  }
}
</script>