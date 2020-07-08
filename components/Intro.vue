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
  </b-container>
</template>

<script>
export default {};
</script>

<style lang="scss" scoped>
section {
  width: 100%;
}
.img {
  display: block;
  max-width: 100%;
  box-shadow: $bs;
}

.title {
  font-weight: $fw-reg;
  @include font-size(4rem);
}
.title strong {
  display: block;
}
.subtitle {
  background: $clr-accent;
  font-family: $ff-secondary;
  @include font-size(1.75rem);
  padding: 0.25em 1em;
  margin-bottom: 1em;
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
  }

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
</style>
