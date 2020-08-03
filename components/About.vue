<template>
  <b-container>
    <section class="about-me text-center text-md-left">
      <h2 class="section_title section_about">{{ $t('who') }}</h2>
      <p class="section_subtitle subtitle">
        {{ $t('belgian') }}
      </p>

      <div class="about-me_body">
        <p>
          {{ $t('present1') }}
        </p>
        <p>
          {{ $t('present2') }}
        </p>
        <!-- CV Link -->
        <a
          :href="$i18n.locale == 'en' ? linkCV.en : linkCV.fr"
          class="mb-3 d-inline-block"
          target="_blank"
          download
          ><font-awesome-icon :icon="['fas', 'download']" />
          {{ $t('resume') }}</a
        >
        <!-- See Work link -->
        <p>
          {{ $t('check') }}
          <a @click="$emit('seeWork')" class="seeWork text-right" href="#">
            {{ $t('developed') }}
            <font-awesome-icon :icon="['fas', 'arrow-right']" class="arrow" />
          </a>
        </p>
        <!-- Technologies -->
        <h3 class="mb-3">{{ $t('technos') }}</h3>
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
      linkCV: {
        en: 'https://nicolas-vastrade.tk/CV_EN.pdf',
        fr: 'https://nicolas-vastrade.tk/CV_FR.pdf',
      },
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
          name: 'Bootstrap Vue',
          img: require('~/assets/img/logos/bootstrapVue.png'),
        },
        {
          id: 10,
          name: 'WordPress',
          img: require('~/assets/img/logos/wordpress.png'),
        },
        { id: 11, name: 'Git', img: require('~/assets/img/logos/git.png') },
        {
          id: 12,
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
    font-size: 1rem;
  }
}

.seeWork {
  .arrow {
    padding-left: 0.3rem;
    vertical-align: -0.125em;
  }
}

@media (min-width: 768px) {
  .about-me {
    .subtitle {
      padding-left: 2rem;
    }

    .techLogos {
      flex: 0 0 11%;
    }
  }
  .about-me_body {
    p,
    a {
      font-size: 1.25rem;
    }
  }
}
</style>
