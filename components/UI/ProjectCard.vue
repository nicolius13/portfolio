<template>
  <b-col class="d-flex align-items-stretch" md="6">
    <b-card
      :img-src="project.imgSrc"
      :img-alt="project.imgAlt"
      class="work_cards"
      footer-class="work_footer"
      img-top
    >
      <b-card-title class="card_title">
        <a :href="project.liveLink" target="_blank">
          {{ title }}
        </a>
      </b-card-title>
      <b-card-text>
        {{
          $i18n.locale == 'en' ? project.description_en : project.description_fr
        }}
      </b-card-text>
      <b-badge
        v-for="techno in project.technos"
        :key="techno"
        variant="info"
        class="mr-2"
      >
        {{ techno }}
      </b-badge>

      <template v-slot:footer>
        <a v-if="project.liveLink" :href="project.liveLink" target="_blank">
          <font-awesome-icon :icon="['fas', 'eye']" />
          {{ $t('see') }}
        </a>
        <a v-if="project.codeLink" :href="project.codeLink" target="_blank">
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
  computed: {
    title() {
      if (this.project.title_fr && this.$i18n.locale === 'fr') {
        return this.project.title_fr;
      } else {
        return this.project.title;
      }
    },
  },
};
</script>

<style lang="scss" scoped>
.work_cards {
  margin: 1em 0;

  .card_title {
    color: $clr-accent2;
  }
}

.work_footer {
  background-color: $clr-light;
  border-top: none;

  a {
    padding-right: 1em;
  }
}
</style>
