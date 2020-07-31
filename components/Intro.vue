<template>
  <b-container ref="container" class="section intro text-center text-md-left">
    <b-row>
      <b-col>
        <b-row>
          <b-col cols="12">
            <vue-typed-js
              :strings="[$t('hello')]"
              class="d-flex justify-content-center justify-content-md-start"
            >
              <h1 class="section_title title typing"></h1>
            </vue-typed-js>
          </b-col>
        </b-row>
        <b-row>
          <b-col cols="12">
            <vue-typed-js
              :strings="['Nicolas Vastrade']"
              class="d-flex justify-content-center justify-content-md-start"
            >
              <h1 class="section_title title font-weight-bold typing"></h1>
            </vue-typed-js>
          </b-col>
        </b-row>
        <b-row>
          <b-col>
            <p :style="width" class="section_subtitle subtitle">
              Front-end Developer
            </p>
          </b-col>
        </b-row>
        <b-row v-if="windowWidth > 758">
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
      <b-col v-if="windowWidth < 758">
        <SocialLinks />
      </b-col>
    </b-row>
    <div class="text-center text-md-right mt-5">
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
import SocialLinks from './UI/SocialLinks';
export default {
  components: {
    SocialLinks,
  },
  data() {
    return {
      subWidth: 0,
      windowWidth: 0,
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
  mounted() {
    this.subWidth = this.$refs.container.clientWidth;
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
    window.onresize = () => {
      this.windowWidth = window.innerWidth;
      this.calcWidth();
    };
  },
  methods: {
    calcWidth() {
      this.subWidth = this.$refs.container.clientWidth;
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

  .seeWork {
    margin: 0 auto;
    max-width: 740px;
  }
}
</style>
