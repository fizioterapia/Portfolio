<template>
  <a :href="repoUrl">
    <div class="header">
      <div class="project-name"><i class="fab fa-github"></i> {{ name }}</div>
      <div class="language">{{ language }}</div>
    </div>
  </a>
</template>

<script>
export default {
  name: "Project",
  props: {
    name: String,
    desc: String,
    repoUrl: String,
    language: String,
  },
};
</script>

<style lang="scss" scoped>
a {
  padding: 1em;
  background-color: rgba(0, 0, 0, 0.075);
  color: white;

  display: flex;
  align-items: center;
  justify-content: center;

  text-decoration: none;

  animation: popUp 0.3s ease-in-out;
  transition: 0.3s all ease-in-out;

  .header {
    .project-name {
      display: block;
      font-size: 1.25em;
      font-weight: 700;
    }

    .language {
      margin: 0.5em;
      display: inline-block;
      border-radius: 0.25em;
      padding: 0.25em 0.5em;
      background-color: rgba(255, 255, 255, 0.1);
    }

    overflow: auto;
  }

  .project-description {
    width: 75%;
    margin: 0 auto;
    padding: 0.5em;
    text-decoration: none;
  }
}

a:hover {
  transform: scale(1.25);
  background-color: rgba(255, 255, 255, 0.05);
}

@keyframes popUp {
  from {
    transform: scale(0);
    opacity: 0;
  }
  to {
    transform: scale(1);
    opacity: 1;
  }
}
</style>
