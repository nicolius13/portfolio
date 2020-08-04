<template>
  <b-container class="content">
    <b-tabs v-model="tabIndex" content-class="mt-3" align="center">
      <b-overlay
        :show="loading"
        class="loadingOver"
        opacity="1"
        spinner-variant="primary"
      >
        <!-- INTRO Tab -->
        <b-tab
          ref="tab-0"
          @update:active="updateDimension($event, 'tab-0')"
          active
        >
          <template v-slot:title>
            <font-awesome-icon
              :icon="['fas', 'home']"
              v-b-popover.hover.top="'Home'"
            />
          </template>
          <Intro
            :loading="loading"
            :windowWidth="windowWidth"
            @seeWork="tabIndex = 1"
          />
        </b-tab>
        <!-- WORK Tab -->
        <b-tab ref="tab-1" @update:active="updateDimension($event, 'tab-1')">
          <template v-slot:title>
            <font-awesome-icon
              :icon="['fas', 'folder']"
              v-b-popover.hover.top="'My Work'"
            />
          </template>
          <Work />
        </b-tab>
        <!-- ABOUT Me Tab -->
        <b-tab ref="tab-2" @update:active="updateDimension($event, 'tab-2')">
          <template v-slot:title>
            <font-awesome-icon
              :icon="['fas', 'address-card']"
              v-b-popover.hover.top="'About Me'"
            />
          </template>
          <About @seeWork="tabIndex = 1" />
        </b-tab>
        <!-- CONTACT Tab -->
        <b-tab ref="tab-3" @update:active="updateDimension($event, 'tab-3')">
          <template v-slot:title>
            <font-awesome-icon
              :icon="['fas', 'envelope']"
              v-b-popover.hover.top="'Contact Me'"
            />
          </template>
          <Contact />
        </b-tab>
      </b-overlay>
    </b-tabs>
    <ScrollTop />
    <Footer @langChange="updateDimension(true, `tab-${tabIndex}`)" />
  </b-container>
</template>

<script>
import Intro from '@/components/Intro';
import About from '@/components/About';
import Work from '@/components/Work';
import Contact from '@/components/Contact';
import ScrollTop from '@/components/UI/ScrollTop';
import Footer from '@/components/Footer';

export default {
  components: {
    Intro,
    About,
    Work,
    Contact,
    ScrollTop,
    Footer,
  },
  data() {
    return {
      tabIndex: 0,
      windowWidth: 0,
      loading: true,
    };
  },
  mounted() {
    // calc the window size on window load once
    window.addEventListener(
      'load',
      () => {
        // get the screen width
        this.windowWidth = window.innerWidth;
        // Stop the loader
        this.loading = false;
        // calculate the tab height
        this.updateDimension(true, 'tab-0');
      },
      {
        once: true,
      }
    );

    // add event listener on window resize
    window.onresize = () => {
      this.windowWidth = window.innerWidth;
      this.updateDimension(true, `tab-${this.tabIndex}`);
    };
  },
  methods: {
    updateDimension($event, tab) {
      if ($event === true) {
        setTimeout(() => {
          const newTab = this.$refs[tab].$el;
          const tabContent = document.getElementsByClassName('tab-content')[0];
          // set max/min height
          const height = `calc(${newTab.clientHeight}px + 4rem`;
          tabContent.style.maxHeight = height;
          tabContent.style.minHeight = height;
        }, 10);
      }
    },
  },
};
</script>

<style lang="scss">
.content {
  margin-top: 2.25rem;
}
.nav-tabs {
  border: none;
}

.nav-tabs .nav-link {
  position: relative;
  display: inline-block;
  color: $clr-light;
  opacity: 0.4;
  border: none;
  @include font-size(2.8rem);
  margin: 0 0.25em 0 0.25em;
  transition: opacity 0.25s ease-in-out;
}
.nav-tabs .nav-link:hover {
  opacity: 1;
}

.nav-tabs .nav-link.active {
  color: $clr-light;
  background: none;
  opacity: 1;
}

.nav-tabs .nav-link::after {
  content: '';
  position: absolute;
  display: block;
  bottom: -1rem;
  margin: auto;
  border-bottom: 0rem solid $clr-light;
  border-left: solid transparent;
  @include rfs(1.5rem, border-left-width);
  border-right: solid transparent;
  @include rfs(1.5rem, border-right-width);
  transition: border-bottom-width 0.25s ease-in-out;
}

@media screen and (max-width: 700px) {
  .nav-tabs .nav-link::after {
    left: 0.75rem;
  }
}

.nav-tabs .nav-link.active::after {
  @include rfs(1.5rem, border-bottom-width);
}

.popover {
  top: -5px !important;
}
</style>
