<template>
  <b-container>
    <section id="home" class="intro text-center text-md-left">
      <h1 class="section_title title">
        Hi, I m <strong>Nicolas Vastrade</strong>
      </h1>
      <p class="section_subtitle subtitle">
        Front-end Dev
      </p>

      <img
        class="img"
        src="../assets/img/portrait.JPG"
        alt="A photo of me :)"
      />
    </section>

    <a @click="$emit('seeWork')" class="seeWork text-right" href="#">
      Come and see what I can do
      <font-awesome-icon :icon="['fas', 'arrow-right']" class="arrow" />
    </a>
  </b-container>
</template>

<script>
export default {};
</script>

<style lang="scss" scoped>
.title {
  font-weight: $fw-reg;
  @include font-size(4rem);

  strong {
    display: block;
  }
}

.img {
  display: block;
  max-width: 100%;
  box-shadow: $bs;
}

.subtitle {
  background: $clr-accent;
  font-family: $ff-secondary;
  @include font-size(1.75rem);
  padding: 0.25em 1em;
  margin-bottom: 1em;
}

.seeWork {
  display: block;
  @include font-size(1.75rem);

  .arrow {
    padding-left: 0.5em;
    width: inherit;
    transition: all 0.25s ease-in-out;
  }

  &:hover {
    text-decoration: none;
  }

  &:hover .arrow {
    transform: translateX(0.5em);
  }
}

@media (min-width: 768px) {
  .intro {
    display: grid;
    width: min-content;
    margin: 0 auto;
    grid-column-gap: 1em;
    grid-template-areas:
      'img title'
      'img subtitle';
    grid-template-columns: min-content max-content;

    .img {
      grid-area: img;
      min-width: 250px;
      position: relative;
      z-index: 2;
    }

    .subtitle {
      align-self: start;
      grid-column: -1 / 1;
      grid-row: 2;
      text-align: right;
      position: relative;
      left: -1.5em;
      width: calc(100% + 1.5em);
    }
  }
}
</style>
