<template>
  <footer class="d-flex justify-content-center">
    <ul class="social-list">
      <li class="social-list_item">
        <p>Nicolas Vastrade</p>
      </li>
      <li class="social-list_item">
        <a
          target="_blank"
          class="social-list_link icon"
          href="https://github.com/nicolius13"
        >
          <font-awesome-icon :icon="['fab', 'github-square']" />
        </a>
      </li>
      <li class="social-list_item">
        <a
          target="_blank"
          class="social-list_link icon"
          href="https://www.linkedin.com/in/nicolas-vastrade"
        >
          <font-awesome-icon :icon="['fab', 'linkedin']" />
        </a>
      </li>
      <li class="social-list_item">
        <p>{{ $t('design') }}</p>
        <a target="_blank" class="social-list_link" href="http://html5up.net"
          >HTML5 UP</a
        >
      </li>
      <li class="social-list_item">
        <nuxt-link
          v-for="locale in availableLocales"
          :key="locale.code"
          :to="switchLocalePath(locale.code)"
        >
          {{ $t('language') }} {{ locale.name }}
        </nuxt-link>
      </li>
    </ul>
  </footer>
</template>

<script>
export default {
  computed: {
    availableLocales() {
      return this.$i18n.locales.filter(i => i.code !== this.$i18n.locale);
    },
  },
};
</script>

<style lang="scss" scoped>
footer {
  color: $clr-light;

  p {
    opacity: 0.45;
    display: inline-block;
  }
}
.social-list {
  list-style: none;
  padding: 0;
  margin-top: 2em;

  .social-list_item {
    display: inline-block;
    padding: 0 1em;
  }
  .social-list_link {
    color: $clr-light;
    opacity: 0.5;
    text-decoration: underline;
    transition: opacity 0.25s ease-in-out;
  }
  .icon {
    @include font-size(1.5rem);
  }
  .social-list_link:hover {
    opacity: 0.9;
  }
}
</style>
