<template>
  <section class="contact-form pv6 mbp-pv4">
    <form class="content-container">
      <div class="width-10-col mla mra">
        <h3 class="mb3">Get in touch</h3>
        <div class="mbp-flex-column">
          <label class="radio-btn mr1 mbp-block mbp-mr0 mbp-mb1" v-for="(subject, key) in subjects" :key="key">
            <input type="radio" name="subject" :value="key" v-model="selectedSubject">
            <span class="btn mbp-block mbp-text-center">{{ subject.label }}</span>
          </label>
        </div>
        <input class="mt3 width-6-col" type="text" name="name" placeholder="Name" />
        <input class="mt3 width-6-col" type="text" name="email" placeholder="Email" />
        <input class="mt3 width-6-col" type="text" name="body" :placeholder="selectedPlaceholder" />
        <button class="mt4 btn--filled mbp-block mbp-width-full">Submit</button>
      </div>
    </form>
  </section>
</template>

<static-query>
query {
  metadata {
    siteName
  }
}
</static-query>

<script>

export default {
  data() {
    return {
      selectedSubject: 'design',
      subjects: {
        design: {
          label: 'Design an experience',
          placeholder: 'Bring out the marching band!'
        },
        evaluate: {
          label: 'Evaluate your product',
          placeholder: 'Let\'s address your elephant in the room.'
        },
        chat: {
          label: 'Say hi',
          placeholder: 'What\'s up?'
        }
      },
    }
  },
  computed: {
    selectedPlaceholder() {
      return this.subjects[this.selectedSubject].placeholder;
    }
  },
}
</script>