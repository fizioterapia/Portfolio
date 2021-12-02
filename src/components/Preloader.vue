<template>
  <div id="preloader">
    <div class="inner">
      <div class="dot"></div>
      <div class="dot"></div>
      <div class="dot"></div>
      <div class="dot"></div>
    </div>
  </div>
</template>

<script>
export default {};
</script>

<style lang="scss" scoped>
#preloader {
  width: 100%;
  height: 100%;

  position: fixed;
  pointer-events: none;
  top: 0;
  left: 0;
  z-index: 9999;

  display: flex;

  align-items: center;
  justify-content: center;

  background-color: black;

  transition: 1.5s all ease-in-out;

  .inner {
    position: relative;

    height: 3em;
    width: 16em;

    .dot {
      position: absolute;

      display: inline-block;
      width: 1.5em;
      height: 1.5em;

      background-color: white;

      margin: 0 0em;
      border-radius: 100%;

      animation: preloader 1.5s infinite cubic-bezier(0.39, 0.58, 0.57, 1);
    }

    @for $i from 1 through 4 {
      .dot:nth-child(#{$i}) {
        left: calc(#{($i - 1) * 4}em + 1.5em);
        animation-delay: #{($i - 1) * (1.5/4)}s;
      }
    }
  }

  @keyframes preloader {
    0% {
      top: 0em;
    }

    12.5% {
      top: -1em;
    }

    25% {
      top: 0em;
    }

    100% {
      top: 0em;
    }
  }
}

#preloader.hidden {
  opacity: 0;
}
</style>
