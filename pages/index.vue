<template>
  <div>
    <b-container>
      <b-tabs content-class="mt-3" align="center">
        <b-tab active>
          <template v-slot:title>
            <font-awesome-icon :icon="['fas', 'home']" />
          </template>
          <Intro />
        </b-tab>
        <b-tab>
          <template v-slot:title>
            <font-awesome-icon :icon="['fas', 'folder']" />
          </template>
          <Work />
        </b-tab>
        <b-tab>
          <template v-slot:title>
            <font-awesome-icon :icon="['fas', 'address-card']" />
          </template>
          <About />
        </b-tab>
        <b-tab>
          <template v-slot:title>
            <font-awesome-icon :icon="['fas', 'envelope']" />
          </template>
          Contact me !
        </b-tab>
      </b-tabs>
    </b-container>

    <Footer />
  </div>
</template>

<script>
import Intro from '@/components/Intro';
import About from '@/components/About';
import Work from '@/components/Work';
import Footer from '@/components/Footer';

export default {
  components: {
    Intro,
    About,
    Work,
    Footer,
  },
};
</script>

<style lang="scss">
.nav-tabs {
  border: none;
}

.tab-content {
  padding: 2em;
  background: $clr-light;
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
</style>
