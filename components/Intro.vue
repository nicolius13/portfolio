<template>
  <b-container>
    <section class="intro text-center text-md-left">
      <h1 class="section_title title">
        Hi, I'm <strong>Nicolas Vastrade</strong>
      </h1>
      <p class="section_subtitle subtitle">
        Front-end Dev
      </p>
      <!-- IMG -->
      <img
        class="img"
        src="../assets/img/portrait.JPG"
        alt="A photo of me :)"
      />
      <!-- Social Links -->
      <div
        class="social align-items-center justify-content-center justify-content-md-end d-flex"
      >
        <a
          target="_blank"
          class="social_item icon"
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
          class="social_item cvBtn mr-md-3"
          href="https://nicolas-vastrade.tk/CV_EN.pdf"
          target="_blank"
          download
          variant="info"
          ><font-awesome-icon :icon="['fas', 'download']" /> CV</b-button
        >
      </div>
    </section>
    <a @click="$emit('seeWork')" class="seeWork text-right" href="#">
      Come and see
      <div class="d-bloc d-md-inline">
        what I can do
        <font-awesome-icon :icon="['fas', 'arrow-right']" class="arrow" />
      </div>
    </a>
  </b-container>
</template>

<script>
export default {};
</script>

<style lang="scss" scoped>
.title {
  font-weight: $fw-reg;
  margin-bottom: 0.5rem;

  strong {
    display: block;
  }
}

.img {
  display: block;
  max-width: 100%;
  box-shadow: $bs;
}
.cvDownBtn {
  background: transparent;
  color: $clr-accent2;
  border-color: $clr-accent2;
  transition: all 0.25s ease-in-out;

  &:hover,
  &:active {
    background-color: $clr-accent2;
    border-color: $clr-accent2;
    color: $clr-light;
  }
}
.social {
  line-height: 24px;

  .social_item {
    margin: 2rem 0.8rem;
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

.seeWork {
  display: block;
  @include font-size(1.75rem);

  .arrow {
    padding-left: 0.5rem;
  }
  &:hover {
    text-decoration: none;
  }
}

@media (min-width: 768px) {
  .intro {
    display: grid;
    width: min-content;
    padding-bottom: 3rem;
    margin: 0 auto;
    grid-column-gap: 1rem;
    grid-template-areas:
      'img title'
      'img subtitle'
      'img social';
    grid-template-columns: min-content max-content;

    .img {
      grid-area: img;
      min-width: 250px;
      position: relative;
      z-index: 2;
    }

    .subtitle {
      text-align: right;
      margin-bottom: 1.3rem;
    }
  }

  .social {
    .social_item {
      margin: 0rem 0.8rem;
    }
  }
  .seeWork {
    margin: 0 auto;
    max-width: 740px;
  }
}
</style>
