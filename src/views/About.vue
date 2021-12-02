<template>
  <div class="flex">
    <div>
      <h1>Tomasz Gradek</h1>
      <h3>
        Amateur front-end developer and also college student trying to get
        Bachelor's degree of Computer Science on Faculty of Mathematics and
        Computer Science in University of Lodz
      </h3>
      <h2>My Tech Stack</h2>
      <div class="technology-grid">
        <i class="fab fa-git icon"></i>
        <i class="fab fa-node icon"></i>
        <i class="fab fa-html5 icon"></i>
        <i class="fab fa-css3 icon"></i>
        <i class="fab fa-js icon"></i>
        <i class="fab fa-vuejs icon"></i>
        <i class="fab fa-php icon"></i>
        <i class="fab fa-python icon"></i>
      </div>
    </div>
  </div>
</template>

<script>
export default {};
</script>

<style lang="scss" scoped>
div {
  background-color: #6a3093;
  color: white;
}

h1 {
  font-weight: 700;
  font-size: 3em;

  margin: 0.25em 0;
}

h2 {
  font-size: 2em;
  font-weight: 700;

  margin: 0.75em 0;
}

h3 {
  font-weight: 500;
  margin: 0;
  font-size: 1em;

  width: 66.6%;

  margin: 0.5em auto;
}

.technology-grid {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-evenly;
  font-size: 0.75em;

  .icon {
    margin: 0.5em 0.5em;
  }
}
</style>
