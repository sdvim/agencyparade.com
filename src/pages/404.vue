<template>
  <Layout :showContactForm="false">
    <section class="flex flex-column flex-j-center pv6 mbp-pv4 text-center">
      <div class="pvhh">
        <h1 class="mb2">404</h1>
        <p class="fs-small">Sorry! This page doesn't exist. <g-link to="/">Back to home.</g-link></p>
      </div>
    </section>
  </Layout>
</template>

<script>
export default {
  metaInfo: {
    title: '404'
  },
}
</script>