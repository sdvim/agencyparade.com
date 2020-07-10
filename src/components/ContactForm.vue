<template>
  <section class="contact-form pv6 mbp-pv4">
    <form class="content-container" action="https://formspree.io/xnqggezk" method="POST" @submit="checkForm" ref="form">
      <div class="width-10-col mla mra">
        <h3 class="mb3">Get in touch</h3>
        <div class="mbp-flex-column">
          <label class="radio-btn mr1 mbp-block mbp-mr0 mbp-mb1" v-for="(subject, key) in subjects" :key="key">
            <input type="radio" :value="key" v-model="selectedSubject">
            <span class="btn mbp-block mbp-text-center">{{ subject.label }}</span>
          </label>
        </div>
        <input type="hidden" :value="selectedSubjectLabel" name="subject">
        <input class="mt3 width-6-col" type="text" ref="name" name="name" v-model="name" placeholder="Name" />
        <p class="error" v-if="error.name">Please include your name.</p>
        <input class="mt3 width-6-col" type="text" ref="email" name="email" v-model="email" placeholder="Email" />
        <p class="error" v-if="error.email">Please provide a valid email address.</p>
        <input class="mt3 width-6-col" type="text" ref="body" name="body" v-model="body" :placeholder="selectedPlaceholder" />
        <p class="error" v-if="error.body">Please say what ya gotta say!</p>
        <button :disabled="submitted" class="mt4 btn--filled mbp-block mbp-width-full">{{ submitted ? 'Submitted!' : 'Submit'}}</button>
      </div>
    </form>
  </section>
</template>

<script>
export default {
  data() {
    return {
      name: '',
      email: '',
      body: '',
      error: {},
      submitted: false,
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
    selectedSubjectLabel() {
      return this.subjects[this.selectedSubject].label;
    },
    selectedPlaceholder() {
      return this.subjects[this.selectedSubject].placeholder;
    },
    validEmail() {
      const re = /^(([^<>()\[\]\\.,;:\s@"]+(\.[^<>()\[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
      return re.test(String(this.email).toLowerCase());
    },
    disabled() {
      return !(this.name && this.validEmail && this.body);
    }
  },
  methods: {
    checkForm(e) {
      e.preventDefault();

      if (this.name && this.validEmail && this.body) {
        const data = new FormData(this.$refs.form);
        const xhr = new XMLHttpRequest();
        xhr.open(this.$refs.form.method, this.$refs.form.action);
        xhr.setRequestHeader('Accept', 'application/json');
        xhr.onreadystatechange = function() {
          if (xhr.readyState !== XMLHttpRequest.DONE) return;
          if (xhr.status === 200) {
            // console.log(xhr.response, xhr.responseType);
            this.submitted = true;
          } else {
            // console.error(xhr.status, xhr.response, xhr.responseType);
            this.submitted = false;
          }
        };
        xhr.send(data);
        this.submitted = true;
      };

      this.error = {};
      if (!this.body) {
        this.error.body = true;
        this.$refs.body.focus();
      }
      if (!this.email || !this.validEmail) {
        this.error.email = true;
        this.$refs.email.focus();
      }
      if (!this.name) {
        this.error.name = true;
        this.$refs.name.focus();
      }
    },
  }
}
</script>