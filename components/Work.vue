<template>
  <b-container>
    <section id="work" class="my-work">
      <h2 class="section_title">My work</h2>
      <b-row>
        <ProjectCard
          v-for="project in projects"
          :key="project.title"
          :project="project"
        />
      </b-row>
    </section>
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
          description:
            'Project 7 created for the Front-End developer path of OpenClassroom: Launch your own restaurant review site.',
          liveLink: 'https://nicolius13.github.io/resto_rating',
          codeLink: 'https://github.com/nicolius13/resto_rating',
        },
        //  Projet Bambous.be
        {
          title: 'Bambous.be',
          imgSrc: require('~/assets/img/work/bambous.jpg'),
          imgAlt: 'bambous.be website',
          description:
            'Redesign and switching of bambous.be web site to WordPress',
          liveLink: 'https://bambous.be/',
        },
        // Projet Dungeon
        {
          title: 'Dungeon',
          imgSrc: require('~/assets/img/work/Dungeon.jpg'),
          imgAlt: 'Dungeon game',
          description:
            'Project 6 created for the Front-End developer path of OpenClassroom: Build a turn-based board game in JavaScript.',
          liveLink: 'https://nicolius13.github.io/Dungeon_code',
          codeLink: 'https://github.com/nicolius13/Dungeon_code',
        },
        // Projet Testing Todos
        {
          title: 'Enhance an existing project',
          imgSrc: require('~/assets/img/work/testing_todos.png'),
          imgAlt: 'Todo App',
          description:
            'Project 8 created for the Front-End developer path of OpenClassroom: Enhance an existing project.',
          liveLink: 'https://nicolius13.github.io/testing-todo',
          codeLink: 'https://github.com/nicolius13/testing-todo',
        },
        // Projet Quotes Generator
        {
          title: 'Quotes Generator',
          imgSrc: require('~/assets/img/work/quotes_generator.png'),
          imgAlt: 'Quotes generator',
          description:
            'Project 5 created for the Front-End developer path of OpenClassroom: Create a quotes generator.',
          liveLink: 'https://nicolius13.github.io/Quotes-generator',
          codeLink: 'https://github.com/nicolius13/Quotes-generator',
        },
        // Projet Film Festival
        {
          title: "Analyze a client's needs",
          imgSrc: require('~/assets/img/work/film_festival.jpg'),
          imgAlt: 'film festival website',
          description:
            "Project 3 created for the Front-End developer path of OpenClassroom: Analyze a client's needs for their film festival.",
          liveLink: 'https://nicolius13.github.io/simple-film-festival-website',
          codeLink:
            'https://github.com/nicolius13/simple-film-festival-website',
        },
        // Projet Express Food
        {
          title: 'Map out a technical solution',
          imgSrc: require('~/assets/img/work/express_food.png'),
          imgAlt: 'express food doc',
          description:
            'Project 4 created for the Front-End developer path of OpenClassroom: Map out a technical solution for the food delivery site ExpressFood.',

          codeLink: 'https://github.com/nicolius13/express_food',
        },
      ],
    };
  },
};
</script>

<style lang="scss" scoped>
.section_title {
  color: $clr-accent;
  font-weight: $fw-bold;
  @include font-size(4rem);
  margin-bottom: 2rem;
}
</style>
