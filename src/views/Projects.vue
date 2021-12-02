<template>
  <div class="flex">
    <div style="width: 100%">
      <h1>My projects</h1>
      <div class="projects">
        <Project
          v-for="repository in repositories"
          :key="repository.id"
          :name="repository.name"
          :desc="repository.description"
          :language="repository.language"
          :repoUrl="repository.html_url"
        >
        </Project>
      </div>
    </div>
  </div>
</template>

<script>
import Project from "../components/Project.vue";

export default {
  data: () => {
    return {
      repositories: [],
    };
  },
  async mounted() {
    const response = await fetch(
      "https://api.github.com/users/fizioterapia/repos"
    );
    this.repositories = await response.json();
    this.repositories = this.repositories.filter((value) => {
      return ["JavaScript", "Vue", "HTML"].includes(value.language);
    });

    console.log(this.repositories);
  },
  components: {
    Project,
  },
};
</script>

<style lang="scss" scoped>
h1,
h2 {
  margin: 0;
}

h1 {
  font-weight: 700;
  font-size: 3em;

  margin: 1em 0;
  color: white;
}

.flex {
  background-color: #a044ff;

  width: 100%;
  height: 100%;
}

.projects {
  display: flex;
  flex-wrap: wrap;

  align-items: stretch;
  justify-content: space-around;

  width: 50%;
  margin: 0 auto;

  a {
    width: 40%;
    margin: 5%;
    height: inherit;

    box-sizing: border-box;
  }
}

@media only screen and (max-width: 768px) {
  .projects {
    width: 100%;
  }
}
</style>
