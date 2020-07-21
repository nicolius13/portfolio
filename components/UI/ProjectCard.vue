<template>
  <b-col class="d-flex align-items-stretch" md="6" lg="4">
    <b-card
      :title="project.title"
      :img-src="project.imgSrc"
      :img-alt="project.imgAlt"
      class="work_cards"
      footer-class="work_footer"
      img-top
    >
      <b-card-text>
        {{ project.description }}
      </b-card-text>

      <template v-slot:footer>
        <a v-if="project.liveLink" :href="project.liveLink" target="blank">
          <font-awesome-icon :icon="['fas', 'eye']" />
          See Live
        </a>
        <a v-if="project.codeLink" :href="project.codeLink" target="blank">
          <font-awesome-icon :icon="['fab', 'github']" />
          Code
        </a>
      </template>
    </b-card>
  </b-col>
</template>

<script>
export default {
  props: {
    project: {
      type: Object,
      default: () => {
        return {};
      },
    },
  },
};
</script>

<style lang="scss" scoped>
.work_cards {
  margin: 1em 0;
}

.work_footer {
  background-color: $clr-light;
  border-top: none;

  a {
    padding-right: 1em;
    color: $clr-accent2;
    transition: all 0.25s ease-in-out;
  }
  a:hover {
    color: $clr-accent;
  }
}
</style>
