<template>
  <section class="contact-form">
    <form class="content">
      <h3>Get in touch</h3>
      <div>
        <label class="contact-form__btn" v-for="(subject, key) in subjects" :key="key">
          <input type="radio" name="subject" :value="key" v-model="selectedSubject">
          <span class="btn">{{ subject.label }}</span>
        </label>
      </div>
      <input type="text" name="name" placeholder="Name" />
      <input type="text" name="email" placeholder="Email" />
      <input type="text" name="body" :placeholder="selectedPlaceholder" />
      <button class="btn--filled">Submit</button>
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

<style lang="scss">
.contact-form {
  padding: 6.666rem calc(2 * var(--space)) 6rem;
  &__btn {
    margin-right: 1rem;
    &:last-child {
      margin-right: 0;
    }
    input {
      display: none;
      &:checked + span {
        box-shadow: 0 0 0 1px currentColor inset;
      }
    }
    span {
      box-shadow: 0 0 0 1px var(--border-color) inset;
      transition: box-shadow .6s cubic-bezier(0.175, 0.885, 0.32, 1.275);
    }
  }
  h3 {
    margin-bottom: 2.666rem;
  }
  input[type="text"] {
    width: 100%;
    max-width: 48.5rem;
    margin-top: 3rem;
  }
  button {
    margin-top: 4.5rem;
  }
}
</style>
