<template>
  <div class="wrapper">
    <nuxt />
  </div>
</template>

<style>
.wrapper {
  min-height: calc(100vh - 2.25rem);
}

.wrapper::after {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  bottom: 0;
  right: 0;
  z-index: -1;
  background: url('~assets/img/code_back1.jpg');
  background-size: cover;
  opacity: 0.25;
}
</style>
