<template>
  <b-container>
    <section id="about" class="about-me text-center text-md-left">
      <h2 class="section_title section_about">Who I am</h2>
      <p class="section_subtitle subtitle">Front-end developer based in Laos</p>

      <div class="about-me_body">
        <p>
          Hello, i'm Nicolas Vastrade, i'm specialize in Vue.Js/Nuxt.js web app.
          But I can a lot of other thinks also.
        </p>
        <p>Technologie that I know</p>
        <b-row align-v="center" align-h="center">
          <b-col
            v-for="logo in logos"
            :key="logo.id"
            class="techLogos m-2 m-md-3"
            cols="3"
          >
            <b-img :src="logo.img" fluid></b-img>
          </b-col>
        </b-row>
      </div>
    </section>
  </b-container>
</template>

<script>
export default {
  data() {
    return {
      logos: [
        { id: 1, img: require('~/assets/img/logos/html.png') },
        { id: 2, img: require('~/assets/img/logos/css.png') },
        { id: 3, img: require('~/assets/img/logos/sass.png') },
        { id: 4, img: require('~/assets/img/logos/js.png') },
        { id: 5, img: require('~/assets/img/logos/jQuery.png') },
        { id: 6, img: require('~/assets/img/logos/bootstrap.png') },
        { id: 7, img: require('~/assets/img/logos/vue.png') },
        { id: 8, img: require('~/assets/img/logos/nuxt.png') },
        { id: 9, img: require('~/assets/img/logos/wordpress.png') },
        { id: 10, img: require('~/assets/img/logos/git.png') },
        { id: 11, img: require('~/assets/img/logos/github.png') },
      ],
    };
  },
};
</script>

<style lang="scss" scoped>
.section_title {
  font-weight: $fw-bold;
  @include font-size(4rem);
  margin-bottom: 0.5rem;
}

@media (min-width: 768px) {
  .about-me {
    max-width: 740px;
    margin: 0 auto;

    .subtitle {
      padding-left: 1.5em;
    }

    .techLogos {
      flex: 0 0 11%;
    }
  }
}
</style>
