<template>
  <b-container ref="container" class="section intro text-center text-md-left">
    <b-row>
      <b-col>
        <b-row>
          <b-col cols="12">
            <h1 class="section_title title typerHello"></h1>
          </b-col>
        </b-row>
        <b-row>
          <b-col class="d-flex align-items-center" cols="12">
            <h1
              class="section_title title d-inline-block font-weight-bold typerName"
            ></h1>
          </b-col>
        </b-row>
        <b-row>
          <b-col>
            <p :style="width" class="section_subtitle subtitle">
              Front-end Developer
            </p>
          </b-col>
        </b-row>
        <b-row v-if="windowWidth > 768">
          <SocialLinks />
        </b-row>
      </b-col>
      <!-- img -->
      <b-col class="d-flex align-items-center" md="4">
        <b-img
          fluid
          class="img"
          src="../assets/img/portrait.JPG"
          alt="A photo of me :)"
        />
      </b-col>
      <b-col v-if="windowWidth < 768">
        <SocialLinks />
      </b-col>
    </b-row>
    <div class="text-center text-md-right mt-2 mt-md-5">
      <a @click="$emit('seeWork')" class="seeWork text-right" href="#">
        {{ $t('come') }}
        <div class="d-bloc d-md-inline text-center">
          {{ $t('canDo') }}
          <font-awesome-icon :icon="['fas', 'arrow-right']" class="arrow" />
        </div>
      </a>
    </div>
  </b-container>
</template>

<script>
import Typed from 'typed.js';
import SocialLinks from './UI/SocialLinks';

export default {
  components: {
    SocialLinks,
  },
  data() {
    return {
      subWidth: 0,
      windowWidth: 0,
      typerOptions: {},
      typerHello: null,
      typerName: null,
    };
  },
  computed: {
    width() {
      if (this.windowWidth > 768) {
        return { width: this.subWidth + 32 + 'px' };
      } else {
        return { width: 'auto' };
      }
    },
  },

  watch: {
    '$i18n.locale'(newValue, oldValue) {
      this.resetTyper('typerHello');
      this.resetTyper('typerName');
    },
  },

  mounted() {
    // calc the container size
    this.subWidth = this.$refs.container.clientWidth;
    // calc the window size on window load once
    window.addEventListener(
      'load',
      () => {
        this.windowWidth = window.innerWidth;
        this.calcWidth();
      },
      {
        once: true,
      }
    );
    // add event listener on window resize
    window.onresize = () => {
      this.windowWidth = window.innerWidth;
      this.calcWidth();
    };

    this.resetTyper('typerHello');
    this.resetTyper('typerName');
  },
  methods: {
    calcWidth() {
      this.subWidth = this.$refs.container.clientWidth;
    },
    resetTyper(typer) {
      // Destroy if the typer exist
      if (this[typer]) {
        this[typer].destroy();
      }
      // defined the options depending of the typer
      let options;
      if (typer === 'typerHello') {
        options = {
          strings: [this.$t('hello')],
          showCursor: false,
        };
      } else {
        let delay;
        if (this.$i18n.locale === 'en') {
          delay = 370;
        } else {
          delay = 700;
        }
        options = {
          strings: ['Nicolas Vastrade'],
          startDelay: delay,
        };
      }
      // Create the typer
      this[typer] = new Typed(`.${typer}`, options);
    },
  },
};
</script>

<style lang="scss" scoped>
.section {
  padding-bottom: 0;
}
.title {
  font-weight: $fw-reg;
  margin-bottom: 0.5rem;
  @include rfs(4rem, height);
}

.img {
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

.seeWork {
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
    .img {
      z-index: 99;
    }

    .subtitle {
      margin-left: -1rem;
      margin-right: -1rem;
      margin-bottom: 1.3rem;
    }
  }
}
</style>
