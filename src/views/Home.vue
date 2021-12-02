<template>
  <div class="container">
    <div class="about-me">
      <i class="fab fa-html5 icon"></i>
      <div>
        <h1>Tomasz Gradek</h1>
        <h2>Front-end Developer</h2>
      </div>
    </div>

    <div class="slide-information">
      Scroll down for more
      <i class="fas fa-arrow-down"></i>
    </div>
  </div>
</template>

<script>
export default {};
</script>

<style lang="scss" scoped>
.container {
  .about-me {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    text-align: center;
  }
  background: linear-gradient(135deg, #6a3093, #a044ff);
  animation: hueBG 10s infinite linear;

  display: flex;
  justify-content: center;

  flex-direction: column;

  color: white;

  h1,
  h2 {
    margin: 0;
  }

  h1 {
    font-weight: 700;
    font-size: 3em;
  }

  h2 {
    font-weight: 500;
    font-size: 1em;
    text-transform: uppercase;
    letter-spacing: 0.35em;

    color: rgba(255, 255, 255, 0.75);
  }

  .slide-information {
    position: absolute;

    top: 90%;
    left: 50%;

    background: none;

    font-size: 1em;
    filter: drop-shadow(0px 1px 5px rgba(0, 0, 0, 0.1));

    transform: translate(-50%, -50%);
    animation: move 3s infinite ease-in-out;

    text-align: center;
    text-transform: uppercase;
    letter-spacing: 2px;

    svg {
      display: block;
      margin: 8px auto;
    }
  }
}

@keyframes move {
  0% {
    margin-top: 0;
  }

  50% {
    margin-top: -2em;
  }

  100% {
    margin-top: 0;
  }
}

@keyframes hueBG {
  from {
    filter: hue-rotate(0deg);
  }
  to {
    filter: hue-rotate(360deg);
  }
}
</style>
