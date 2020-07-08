<template>
  <div>
    <Header />
    <Intro />
    <About />
    <Work />
    <Footer />
  </div>
</template>

<script>
import Header from '@/components/Header';
import Intro from '@/components/Intro';
import About from '@/components/About';
import Work from '@/components/Work';
import Footer from '@/components/Footer';

export default {
  components: {
    Header,
    Intro,
    About,
    Work,
    Footer,
  },
};
</script>

<style></style>
