<template>
  <b-col
    class="social align-items-center justify-content-center justify-content-md-start d-flex"
  >
    <a
      target="_blank"
      class="social_item icon first"
      href="https://www.linkedin.com/in/nicolas-vastrade"
    >
      <font-awesome-icon :icon="['fab', 'linkedin']" />
    </a>
    <a
      target="_blank"
      class="social_item icon"
      href="https://github.com/nicolius13"
    >
      <font-awesome-icon :icon="['fab', 'github-square']" />
    </a>
    <b-button
      :href="$i18n.locale == 'en' ? linkCV.en : linkCV.fr"
      class="social_item cvBtn mr-md-3"
      target="_blank"
      download
      variant="info"
      ><font-awesome-icon :icon="['fas', 'download']" /> CV</b-button
    >
  </b-col>
</template>

<script>
export default {
  data() {
    return {
      linkCV: {
        en: 'https://nicolas-vastrade.tk/CV_EN.pdf',
        fr: 'https://nicolas-vastrade.tk/CV_FR.pdf',
      },
    };
  },
};
</script>

<style lang="scss" scoped>
.social {
  line-height: 24px;

  .social_item {
    margin: 2rem 0.8rem;

    &.first {
      margin-left: 0;
    }
  }

  .icon {
    font-size: 2.5rem;
  }

  .cvBtn {
    &:hover {
      background-color: $clr-accent;
      border-color: $clr-accent;
    }
  }
}

@media (min-width: 768px) {
  .social {
    .social_item {
      margin: 0rem 0.8rem;
    }
  }
}
</style>
