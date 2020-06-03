<template>
  <div id="app">

    <header class="header content-container">
      <div class="header__left">
        <Logo />
      </div>
      
      <div class="header__right">        
        <g-link class="btn btn--filled" to="/contact">Contact</g-link>
      </div>
    </header>

    <main class="main">
      <slot/>
    </main>

    <ContactForm />

    <footer class="footer">
      <div class="grid">
        <div class="grid__half">
          <Logo />
          <p class="footer__location">Made in Washington DC</p>
        </div>
        <div class="grid__half">
          <a class="footer__email h2" href="mailto:hi@agencyparade.com">hi@agencyparade.com </a>
          <ul class="footer__links">
            <li><a href="/process">Process</a></li>
            <li><a href="/about">About</a></li>
            <li><a href="/contact">Contact</a></li>
          </ul>
        </div>
      </div>
      <div class="footer__copyright">&copy; Agency Parade. All Rights Reserved.</div>
    </footer>

  </div>
</template>

<script>
import ContactForm from '~/components/ContactForm.vue'
import Logo from '~/components/Logo.vue'
import ToggleTheme from '~/components/ToggleTheme.vue'

export default {
  props: {
    showLogo: { default: true }
  },
  components: {
    ContactForm,
    Logo,
    ToggleTheme
  }
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

  .logo {
    transform: translateX(-43%);
    svg {
      height: 3.75rem;
    }
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
}

.footer {
  background: var(--bg-footer);
  color: var(--bg-color);
  font-size: 1.5rem;
  line-height: 1.5555;
  padding: 10rem calc(2 * var(--space)) 4rem;

  .logo {
    margin-bottom: 1rem;
    svg {
      height: 4rem;
    }
  }

  &__location {
    opacity: .5;
    margin-left: calc(var(--grid-width) + var(--grid-gutter));
    margin-left: 95px;
    margin-bottom: 0;
  }

  &__email {
    display: block;
    letter-spacing: -1px;
    margin-bottom: 3.1666rem;
  }

  &__links {
    display: flex;
    list-style: none;
    padding: 0;
    margin: 0;

    li {
      margin: 0;
      min-width: var(--grid-width);
      margin-right: var(--grid-gutter);
    }
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
