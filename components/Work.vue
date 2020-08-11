<template>
  <b-container class="my-work text-center text-md-left">
    <h2 class="section_title">{{ $t('work') }}</h2>
    <b-row>
      <b-col>
        <p class="section_subtitle subtitle">
          {{ $t('make') }}
        </p>
      </b-col>
    </b-row>
    <b-row>
      <ProjectCard
        v-for="project in projects"
        :key="project.title"
        :project="project"
      />
    </b-row>
  </b-container>
</template>

<script>
import ProjectCard from './UI/ProjectCard';
export default {
  components: {
    ProjectCard,
  },
  data() {
    return {
      projects: [
        // Projet Resto Finder
        {
          title: 'Resto Finder',
          imgSrc: require('~/assets/img/work/resto_finder.jpg'),
          imgAlt: 'Resto Finder map',
          description_en:
            'Project 7 created for the Front-End developer path of OpenClassroom: Launch your own restaurant review site.',
          description_fr:
            "7eme projet créé pour le parcours 'Dévelopeur d'application - frontend' d'OpenClassroom : lancez votre propre site d'avis de restaurant",
          technos: ['Nuxt', 'Bootstrap Vue', "Google API's"],
          liveLink: 'https://nicolius13.github.io/resto_rating',
          codeLink: 'https://github.com/nicolius13/resto_rating',
        },
        //  Projet Bambous.be
        {
          title: 'Bambous.be',
          imgSrc: require('~/assets/img/work/bambous.jpg'),
          imgAlt: 'bambous.be website',
          description_en:
            'Redesign and switch to WordPress the bambous.be web site',
          description_fr:
            'Modernisation et passage au CMS Wordpress du site bambous.be',
          technos: ['Wordpress'],

          liveLink: 'https://bambous.be/',
        },
        // Projet Weather app
        {
          title: 'Weather app',
          imgSrc: require('~/assets/img/work/weatherApp.jpg'),
          imgAlt: 'Weather App img',
          description_en:
            'Quick little weather app done for devchallenges.io. I used Nuxt and Bootstrap-Vue to do it. Had real fun coding it :). The weather API used is not really precise btw :)',
          description_fr:
            "Petite application météo rapidement faite pour devchallenges.io. J'ai vraiment eu du plaisir à coder cette app avec Nuxt et Bootstrap-Vue :). L'API météo utilisée n'est pas super précise btw :)",
          technos: ['Nuxt', 'Bootstrap Vue', 'metaweather API'],
          liveLink: 'https://nicolius13.github.io/weather',
          codeLink: 'https://github.com/nicolius13/weather',
        },
        // Projet Dungeon
        {
          title: 'Dungeon',
          imgSrc: require('~/assets/img/work/Dungeon.jpg'),
          imgAlt: 'Dungeon game',
          description_en:
            'Project 6 created for the Front-End developer path of OpenClassroom: Build a turn-based board game in JavaScript.',
          description_fr:
            "6eme projet créé pour le parcours 'Dévelopeur d'application - frontend' d'OpenClassroom : Créez un jeu de plateau tour par tour en JS",
          technos: ['JS', 'JQuery', 'Vue'],
          liveLink: 'https://nicolius13.github.io/Dungeon_code',
          codeLink: 'https://github.com/nicolius13/Dungeon_code',
        },
        // Projet Testing Todos
        {
          title: 'Enhance an existing project',
          title_fr: "Amélioration d'un projet existant",
          imgSrc: require('~/assets/img/work/testing_todos.png'),
          imgAlt: 'Todo App',
          description_en:
            'Project 8 created for the Front-End developer path of OpenClassroom: Enhance an existing project.',
          description_fr:
            "8eme projet créé pour le parcours 'Dévelopeur d'application - frontend' d'OpenClassroom : Reprenez et améliorez un projet existant",
          technos: ['JS', 'Jasmine'],
          liveLink: 'https://nicolius13.github.io/testing-todo',
          codeLink: 'https://github.com/nicolius13/testing-todo',
        },
        // Projet Quotes Generator
        {
          title: 'Quotes Generator',
          title_fr: 'Générateur de citations',
          imgSrc: require('~/assets/img/work/quotes_generator.png'),
          imgAlt: 'Quotes generator',
          description_en:
            'Project 5 created for the Front-End developer path of OpenClassroom: Create a quotes generator.',
          description_fr:
            "5eme projet créé pour le parcours 'Dévelopeur d'application - frontend' d'OpenClassroom : Imaginez un générateur de citation",
          technos: ['JS', 'CSS', 'Bootstrap'],
          liveLink: 'https://nicolius13.github.io/Quotes-generator',
          codeLink: 'https://github.com/nicolius13/Quotes-generator',
        },
        // Projet Film Festival
        {
          title: "Analyze a client's needs",
          title_fr: "Alayse de besoin d'un client",
          imgSrc: require('~/assets/img/work/film_festival.jpg'),
          imgAlt: 'film festival website',
          description_en:
            "Project 3 created for the Front-End developer path of OpenClassroom: Analyze a client's needs for their film festival.",
          description_fr:
            "3eme projet créé pour le parcours 'Dévelopeur d'application - frontend' d'OpenClassroom : Analysez les besoins de votre client pour son festival de films",
          technos: ['JS', 'CSS', 'Bootstrap'],
          liveLink: 'https://nicolius13.github.io/simple-film-festival-website',
          codeLink:
            'https://github.com/nicolius13/simple-film-festival-website',
        },
        // Projet Express Food
        {
          title: 'Map out a technical solution',
          title_fr: 'Conception de solution technique',
          imgSrc: require('~/assets/img/work/express_food.png'),
          imgAlt: 'express food doc',
          description_en:
            'Project 4 created for the Front-End developer path of OpenClassroom: Map out a technical solution for the food delivery site ExpressFood.',
          description_fr:
            "4eme projet créé pour le parcours 'Dévelopeur d'application - frontend' d'OpenClassroom : Concevez la solution technique d'une application de restauration en ligne ExpressFood",

          codeLink: 'https://github.com/nicolius13/express_food',
        },
      ],
    };
  },
};
</script>

<style lang="scss" scoped>
.section_title {
  margin-bottom: 0.5rem;
}

@media (min-width: 768px) {
  .my-work {
    .subtitle {
      padding-left: 2rem;
    }
  }
}
</style>
