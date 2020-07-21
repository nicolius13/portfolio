<template>
  <footer class="d-flex justify-content-center">
    <ul class="social-list">
      <li class="social-list_item">
        <a class="social-list_link" href="mailto:nicolas.vastrade@gmail.com"
          >nicolas.vastrade@gmail.com
        </a>
      </li>
      <li class="social-list_item">
        <a
          target="blank"
          class="social-list_link icon"
          href="https://github.com/nicolius13"
        >
          <font-awesome-icon :icon="['fab', 'github-square']" />
        </a>
      </li>
      <li class="social-list_item">
        <a
          target="blank"
          class="social-list_link icon"
          href="https://www.linkedin.com/in/nicolas-vastrade"
        >
          <font-awesome-icon :icon="['fab', 'linkedin']" />
        </a>
      </li>
      <li class="social-list_item">
        <p>Design idea:</p>
        <a target="blank" class="social-list_link" href="http://html5up.net"
          >HTML5 UP</a
        >
      </li>
    </ul>
  </footer>
</template>

<script>
export default {};
</script>

<style lang="scss" scoped>
footer {
  color: $clr-light;

  p {
    opacity: 0.45;
    display: inline-block;
  }
}
.social-list {
  list-style: none;
  padding: 0;
  margin-top: 2em;

  .social-list_item {
    display: inline-block;
    padding: 0 1em;
  }
  .social-list_link {
    color: $clr-light;
    opacity: 0.5;
    text-decoration: underline;
    transition: opacity 0.25s ease-in-out;
  }
  .icon {
    @include font-size(1.5rem);
  }
  .social-list_link:hover {
    opacity: 0.9;
  }
}
</style>
