<template>
  <div id="app">

    <header class="header content-container" :class="{ isDark }">
      <div class="header__left">
        <Logo />
      </div>
      
      <div class="header__right">        
        <g-link class="btn btn--transparent mr1 mbp-mr0" to="/approach">Our Approach</g-link>
        <g-link class="btn btn--transparent mr1 mbp-mr0" to="/about">About</g-link>
        <g-link class="btn btn--filled mbp-no-btn" to="/contact">Contact</g-link>
      </div>
    </header>

    <main class="main">
      <slot/>
    </main>

    <ContactForm />

    <footer class="footer">
      <div class="grid tbp-flex-column mbp-width-full flex-a-end tbp-flex-a-start">
        <div class="grid__half mbp-width-full">
          <Logo class="mb2 mbp-mb0" />
          <p class="footer__location tbp-mb3 mbp-fs-small">Made in Washington, D.C.</p>
        </div>
        <div class="grid__half mbp-flex mbp-flex-column mbp-width-full">
          <a class="footer__email h2 mb2 mbp-mb0 mbp-mt4" href="mailto:hi@agencyparade.com">hi@agencyparade.com </a>
          <ul class="footer__links mbp-flex-column mbp-flex-o-1">
            <li class="mbp-mb2 mr2"><g-link to="/approach">Our Approach</g-link></li>
            <li class="mbp-mb2 mr2"><g-link to="/about">About</g-link></li>
            <li class="mbp-mb2"><g-link to="/contact">Contact</g-link></li>
          </ul>
        </div>
      </div>
      <div class="footer__copyright mbp-text-left">&copy; Agency Parade. All Rights Reserved.</div>
    </footer>

  </div>
</template>

<script>
import ContactForm from '~/components/ContactForm.vue'
import Logo from '~/components/Logo.vue'

export default {
  props: {
    isDark: { default: false },
    showLogo: { default: true }
  },
  components: {
    ContactForm,
    Logo,
  },
}
</script>

<style lang="scss">
.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  min-height: var(--header-height);
  top: 0;
  left: 0;
  right: 0;
  z-index: 10;
  width: 100%;
  position: absolute;

  &.isDark {
    color: var(--color-white);
  }

  &__left,
  &__right {
    display: flex;
    align-items: center;
  }

  // @media screen and (min-width: 1300px) {
  //   //Make header sticky for large screens
  //   position: sticky;
  //   width: 100%;
  // }
  @media screen and (max-width: 640px) {
    .header__right {
      .btn {
        font-size: 1.25rem;
        padding-right: 1rem;
        padding-left: 1rem;
        &:last-child {
          padding-right: 0;
        }
      }
    }
    .logo svg {
      width: 4rem;
    }
  }
}

.footer {
  background: var(--color-blue);
  color: var(--color-white);
  font-size: 1.5rem;
  line-height: 1.5555;
  padding: 10rem calc(2 * var(--space)) 4rem;

  @media screen and (max-width: 640px) {
    padding: 4rem var(--space);
  }

  .logo {
    svg {
      height: 4rem;
    }
  }

  &__location {
    opacity: .5;
  }

  &__email {
    display: block;
    letter-spacing: -1px;
  }

  &__links {
    display: flex;
    list-style: none;
    padding: 0;
    margin: 0;
  }

  &__copyright {
    font-size: 1.1666rem;
    opacity: .5;
    margin-top: 6rem;
    text-align: center;
  }

  a {
    color: currentColor;
    text-decoration: none;
  }
}
</style>
