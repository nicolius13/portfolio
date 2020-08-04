<template>
  <transition name="btnFade" mode="out-in">
    <b-button v-if="show" @click="goTop" variant="info" class="goTop">
      <font-awesome-icon :icon="['fas', 'arrow-up']" />
    </b-button>
  </transition>
</template>

<script>
export default {
  data() {
    return {
      show: false,
      timeout: null,
    };
  },
  mounted() {
    // listen to scroll event
    window.addEventListener('scroll', this.handleScroll);
  },
  methods: {
    goTop() {
      window.scrollTo({ top: 0, behavior: 'smooth' });
    },
    // set a timeout to not call the fct too much
    handleScroll() {
      if (this.timeout) {
        clearTimeout(this.timeout);
      }
      this.timeout = setTimeout(() => {
        if (window.pageYOffset >= 500) {
          this.show = true;
        } else {
          this.show = false;
        }
      }, 200);
    },
  },
};
</script>

<style lang="scss" scoped>
.goTop {
  position: fixed;
  bottom: 20px;
  right: 20px;
}

// btn is on top of the language switcher between 400px and 360px in french
@media screen and (max-width: 400px) and (min-width: 360px) {
  .goTop {
    bottom: 60px;
  }
}

.btnFade-enter-active,
.btnFade-leave-active {
  transition: opacity 0.5s;
}
.btnFade-enter,
.btnFade-leave-active {
  opacity: 0;
}
</style>
