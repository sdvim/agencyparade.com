<template>
  <section class="contact-form pt6 pb6">
    <form class="content-center">
      <h3 class="mb3">Get in touch</h3>
      <div>
        <label class="radio-btn mr1" v-for="(subject, key) in subjects" :key="key">
          <input type="radio" name="subject" :value="key" v-model="selectedSubject">
          <span class="btn">{{ subject.label }}</span>
        </label>
      </div>
      <input class="mt3 width-6-col" type="text" name="name" placeholder="Name" />
      <input class="mt3 width-6-col" type="text" name="email" placeholder="Email" />
      <input class="mt3 width-6-col" type="text" name="body" :placeholder="selectedPlaceholder" />
      <button class="mt4 btn--filled">Submit</button>
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
          placeholder: 'Stay a while and listen.'
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