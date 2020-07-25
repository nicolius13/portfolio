<template>
  <b-container>
    <section class="about-me text-center text-md-left">
      <h2 class="section_title section_about">Who I am</h2>
      <p class="section_subtitle subtitle">
        Belgian Front-end developer based in Laos
      </p>

      <div class="about-me_body">
        <p>
          Hello, I'm Nicolas Vastrade, I'm a Freelance Developer specialized in
          Vue.Js/Nuxt.js.
        </p>
        <p>
          I used to work as a lab technologist in the pharmaceutical
          industry.When I moved to Senegal I took this opportunity to make a
          career change. I've always been passionate about IT and the web world
          and therefore decided to self-train in web development at first. I
          then followed the ‘Front-end Developer’ Certified Training on
          OpenClassroom. I'm now looking for new projects!
        </p>
        <a class="mb-3 d-block" href="/CV.pdf" download
          ><font-awesome-icon :icon="['fas', 'download']" /> My Resume</a
        >
        <p>
          Come check out what I’ve
          <a @click="$emit('seeWork')" class="seeWork text-right" href="#">
            already developed
            <font-awesome-icon :icon="['fas', 'arrow-right']" class="arrow" />
          </a>
        </p>

        <h3 class="mb-3">Technologies that I use:</h3>
        <b-row align-v="center" align-h="center">
          <b-col
            :id="`popover-${logo.id}-${logo.name}`"
            v-for="logo in logos"
            :key="logo.id"
            class="techLogos m-2 m-md-3"
            cols="3"
          >
            <b-img :src="logo.img" fluid></b-img>
            <b-popover
              :target="`popover-${logo.id}-${logo.name}`"
              :content="logo.name"
              triggers="hover focus"
              placement="top"
              variant="primary"
            ></b-popover>
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
        { id: 1, name: 'HTML', img: require('~/assets/img/logos/html.png') },
        { id: 2, name: 'CSS', img: require('~/assets/img/logos/css.png') },
        { id: 3, name: 'Sass', img: require('~/assets/img/logos/sass.png') },
        {
          id: 4,
          name: 'Javascript',
          img: require('~/assets/img/logos/js.png'),
        },
        {
          id: 5,
          name: 'JQuery',
          img: require('~/assets/img/logos/jQuery.png'),
        },
        {
          id: 6,
          name: 'Bootstrap',
          img: require('~/assets/img/logos/bootstrap.png'),
        },
        { id: 7, name: 'Vue', img: require('~/assets/img/logos/vue.png') },
        { id: 8, name: 'Nuxt', img: require('~/assets/img/logos/nuxt.png') },
        {
          id: 9,
          name: 'WordPress',
          img: require('~/assets/img/logos/wordpress.png'),
        },
        { id: 10, name: 'Git', img: require('~/assets/img/logos/git.png') },
        {
          id: 11,
          name: 'GitHub',
          img: require('~/assets/img/logos/github.png'),
        },
      ],
    };
  },
};
</script>

<style lang="scss" scoped>
.section_title {
  margin-bottom: 0.5rem;
}

.about-me_body {
  p,
  a {
    @include font-size(1.25rem);
  }
}

@media (min-width: 768px) {
  .about-me {
    max-width: 740px;
    margin: 0 auto;

    .subtitle {
      padding-left: 2rem;
    }

    .techLogos {
      flex: 0 0 11%;
    }
  }
}
</style>
