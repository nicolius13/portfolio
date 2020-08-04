<template>
  <b-container class="section intro text-center text-md-left">
    <b-row>
      <b-col class="d-flex flex-column">
        <div class="mt-auto">
          <b-row>
            <!-- Hello -->
            <b-col
              class="d-flex align-items-center justify-content-center justify-content-md-start"
              cols="12"
            >
              <h1 class="section_title title typerHello"></h1>
            </b-col>
          </b-row>
          <b-row>
            <!-- Name -->
            <b-col
              class="d-flex align-items-center justify-content-center justify-content-md-start"
              cols="12"
            >
              <h1 class="section_title title font-weight-bold typerName"></h1>
            </b-col>
          </b-row>
          <b-row>
            <!-- Front-end dev -->
            <b-col class="d-md-none">
              <p :style="width" class="section_subtitle subtitle">
                Front-end Dev
              </p>
            </b-col>
            <b-col class="d-none d-md-block">
              <p :style="width" class="section_subtitle subtitle">
                {{ $t('frontEnd') }}
              </p>
            </b-col>
          </b-row>
        </div>
        <!-- Social links (when screen width > 768px) -->
        <b-row v-if="windowWidth > 768" class="mt-auto">
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
      <!-- social links (when screen width < 768px) -->
      <b-col v-if="windowWidth < 768">
        <SocialLinks />
      </b-col>
    </b-row>
    <!-- Call to action SEE MY WORK -->
    <div class="seeWorkDiv text-center text-md-right">
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
  props: {
    windowWidth: {
      type: Number,
      default: 0,
    },
    loading: {
      type: Boolean,
      default: false,
    },
  },
  data() {
    return {
      subWidth: 0,
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
    // reset the typers on language change
    '$i18n.locale'() {
      this.resetTyper('typerHello', true);
      this.resetTyper('typerName', true);
    },
    // recalculate the subtitle width on window resize
    windowWidth() {
      this.calcWidth();
    },
    loading() {
      if (this.loading === false) {
        // create the typers
        this.resetTyper('typerHello');
        this.resetTyper('typerName');
      }
    },
  },

  methods: {
    calcWidth() {
      // get the tab-content element (available even when intro tab is closed)
      const el = document.getElementsByClassName('tab-content')[0];
      // get the style of that element
      const computedStyle = getComputedStyle(el);
      // calculate the width without padding
      this.subWidth =
        el.clientWidth -
        (parseFloat(computedStyle.paddingLeft) +
          parseFloat(computedStyle.paddingRight));
    },
    resetTyper(typer, reset) {
      //  delay on first load
      let delay = 800;
      // Destroy if the typer exist
      if (reset) {
        this[typer].destroy();
        // no delay when language is changed
        delay = 0;
      }
      // defined the options depending of the typer
      let options;
      if (typer === 'typerHello') {
        options = {
          strings: [this.$t('hello')],
          typeSpeed: 30,
          startDelay: delay,
          onComplete: self => {
            self.cursor.remove();
            this.typerName.start();
          },
        };
      } else {
        options = {
          strings: ['Nicolas Vastrade'],
          typeSpeed: 30,
          onBegin: self => {
            self.stop();
          },
        };
      }
      // Create the typer
      this[typer] = new Typed(`.${typer}`, options);
    },
  },
};
</script>

<style lang="scss" scoped>
.title {
  font-weight: $fw-reg;
  margin-bottom: 0.5rem;
  @include font-size(3rem);
  @include rfs(62px, height);
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

.seeWorkDiv {
  margin-top: 0.5rem;
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
    padding: 3rem 0 0 0;

    .img {
      z-index: 9;
    }

    .title {
      @include font-size(4rem);
      @include rfs(72px, height);
    }

    .subtitle {
      margin-left: -1rem;
      margin-right: -1rem;
      margin-bottom: 1.3rem;
    }
  }
  .seeWorkDiv {
    margin-top: 5rem;
  }
}
</style>
