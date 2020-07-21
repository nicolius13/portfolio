<template>
  <b-container>
    <section id="work" class="my-work">
      <h2 class="section_title">My work</h2>
      <b-row>
        <!-- Projet Resto Finder -->
        <b-col class="d-flex align-items-stretch" md="6" lg="4">
          <b-card
            class="work_cards"
            footer-class="work_footer"
            title="Resto Finder"
            img-src="~/assets/img/work/resto_finder.jpg"
            img-alt="Resto Finder map"
            img-top
          >
            <b-card-text>
              Project 7 created for the Front-End developer path of
              OpenClassroom: Launch your own restaurant review site.
            </b-card-text>

            <template v-slot:footer>
              <a
                href="https://nicolius13.github.io/resto_rating"
                target="blank"
              >
                <font-awesome-icon :icon="['fas', 'eye']" />
                See Live
              </a>
              <a
                href="https://github.com/nicolius13/resto_rating"
                target="blank"
              >
                <font-awesome-icon :icon="['fab', 'github']" />
                Code
              </a>
            </template>
          </b-card>
        </b-col>

        <!-- Projet Bambous.be -->
        <b-col class="d-flex align-items-stretch" md="6" lg="4">
          <b-card
            class="work_cards"
            footer-class="work_footer"
            title="Bambous.be"
            img-src="~/assets/img/work/bambous.jpg"
            img-alt="Resto Finder map"
            img-top
          >
            <b-card-text>
              Modernisation et passage au CMS Wordpress du site bambous.be
            </b-card-text>
            <template v-slot:footer>
              <a href="https://bambous.be/" target="blank">
                <font-awesome-icon :icon="['fas', 'eye']" />
                See Live
              </a>
            </template>
          </b-card>
        </b-col>

        <!-- Projet Dungeon -->
        <b-col class="d-flex align-items-stretch" md="6" lg="4">
          <b-card
            class="work_cards"
            footer-class="work_footer"
            title="Dungeon"
            img-src="~/assets/img/work/Dungeon.jpg"
            img-alt="Dungeon game"
            img-top
          >
            <b-card-text>
              Project 6 created for the Front-End developer path of
              OpenClassroom: Build a turn-based board game in JavaScript.
            </b-card-text>

            <template v-slot:footer>
              <a
                href="https://nicolius13.github.io/Dungeon_code"
                target="blank"
              >
                <font-awesome-icon :icon="['fas', 'eye']" />
                See Live
              </a>
              <a
                href="https://github.com/nicolius13/Dungeon_code"
                target="blank"
              >
                <font-awesome-icon :icon="['fab', 'github']" />
                Code
              </a>
            </template>
          </b-card>
        </b-col>

        <!-- Projet Testing Todos -->
        <b-col class="d-flex align-items-stretch" md="6" lg="4">
          <b-card
            class="work_cards"
            footer-class="work_footer"
            title="Enhance an existing project"
            img-src="~/assets/img/work/testing_todos.png"
            img-alt="Todo App"
            img-top
          >
            <b-card-text>
              Project 8 created for the Front-End developer path of
              OpenClassroom: Enhance an existing project.
            </b-card-text>

            <template v-slot:footer>
              <a
                href="https://nicolius13.github.io/testing-todo"
                target="blank"
              >
                <font-awesome-icon :icon="['fas', 'eye']" />
                See Live
              </a>
              <a
                href="https://github.com/nicolius13/testing-todo"
                target="blank"
              >
                <font-awesome-icon :icon="['fab', 'github']" />
                Code
              </a>
            </template>
          </b-card>
        </b-col>

        <!-- Projet Quotes Generator  -->
        <b-col class="d-flex align-items-stretch" md="6" lg="4">
          <b-card
            class="work_cards"
            footer-class="work_footer"
            title="Qutoes Generator"
            img-src="~/assets/img/work/quotes_generator.png"
            img-alt="Quotes generator"
            img-top
          >
            <b-card-text>
              Project 5 created for the Front-End developer path of
              OpenClassroom: Create a quotes generator.
            </b-card-text>

            <template v-slot:footer>
              <a
                href="https://nicolius13.github.io/Quotes-generator/"
                target="blank"
              >
                <font-awesome-icon :icon="['fas', 'eye']" />
                See Live
              </a>
              <a
                href="https://github.com/nicolius13/Quotes-generator"
                target="blank"
              >
                <font-awesome-icon :icon="['fab', 'github']" />
                Code
              </a>
            </template>
          </b-card>
        </b-col>

        <!-- Projet Film Festival  -->
        <b-col class="d-flex align-items-stretch" md="6" lg="4">
          <b-card
            class="work_cards"
            footer-class="work_footer"
            title="Analyze a client's needs"
            img-src="~/assets/img/work/film_festival.jpg"
            img-alt="film festival website"
            img-top
          >
            <b-card-text>
              Project 3 created for the Front-End developer path of
              OpenClassroom: Analyze a client's needs for their film festival.
            </b-card-text>

            <template v-slot:footer>
              <a
                href="https://nicolius13.github.io/simple-film-festival-website"
                target="blank"
              >
                <font-awesome-icon :icon="['fas', 'eye']" />
                See Live
              </a>
              <a
                href="https://github.com/nicolius13/simple-film-festival-website"
                target="blank"
              >
                <font-awesome-icon :icon="['fab', 'github']" />
                Code
              </a>
            </template>
          </b-card>
        </b-col>

        <!-- Projet Express Food  -->
        <b-col class="d-flex align-items-stretch" md="6" lg="4">
          <b-card
            class="work_cards"
            footer-class="work_footer"
            title="Map out a technical solution"
            img-src="~/assets/img/work/express_food.png"
            img-alt="express food doc"
            img-top
          >
            <b-card-text>
              Project 4 - created for the Front-End developer path of
              OpenClassroom: Map out a technical solution for the food delivery
              site ExpressFood.
            </b-card-text>

            <template v-slot:footer>
              <a
                href="https://github.com/nicolius13/express_food"
                target="blank"
              >
                <font-awesome-icon :icon="['fab', 'github']" />
                Doc
              </a>
            </template>
          </b-card>
        </b-col>
      </b-row>
    </section>
  </b-container>
</template>

<script>
export default {};
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
  }
}
</style>
