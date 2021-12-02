<template>
  <div class="flex">
    <div style="width: 100%; height: 50%">
      <h1>Contact</h1>
      <div class="contact-methods">
        <a class="contact" href="mailto:fizi_design@o2.pl">
          <i class="fas fa-envelope"></i>
          <p>fizi_design@o2.pl</p>
        </a>
        <a class="contact" href="https://t.me/fizioterapia">
          <i class="fab fa-telegram"></i>
          <p>@fizioterapia</p>
        </a>
        <a
          class="contact"
          href="https://www.linkedin.com/in/tomasz-gradek-1342891aa/"
        >
          <i class="fab fa-linkedin"></i>
          <p>Tomasz Gradek</p>
        </a>
        <a class="contact" href="https://www.facebook.com/t.gradek3/">
          <i class="fab fa-facebook"></i>
          <p>Tomasz Gradek</p>
        </a>
      </div>
    </div>
  </div>
</template>

<script>
export default {};
</script>

<style lang="scss" scoped>
.flex {
  background-color: #6a3093;
  color: white;

  .contact-methods {
    display: flex;
    flex-wrap: wrap;

    width: 75%;
    height: 75%;

    margin: 0 auto;

    .contact {
      display: flex;
      flex-direction: column;
      flex-wrap: wrap;

      align-items: center;
      justify-content: center;

      color: white;
      text-decoration: none;

      svg {
        font-size: 2em;
      }

      p {
        font-size: 0.75em;
        font-weight: 500;
      }

      @media only screen and (min-width: 376px) {
        p {
          font-size: 1em;
        }
      }

      width: 47.5%;
      height: 47.5%;
      margin: 1.25%;

      background-color: rgba(0, 0, 0, 0.1);
      transition: 0.3s all ease-in-out;
    }

    .contact:hover {
      background-color: rgba(0, 0, 0, 0.05);
    }
  }
}

h1 {
  font-weight: 700;
  font-size: 3em;
}
</style>
