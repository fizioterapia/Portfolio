<template>
  <Preloader :class="{ hidden: this.showPreloader == false }"></Preloader>
  <nav>
    <router-link to="/">Home</router-link>
    <router-link to="/about">About</router-link>
    <router-link to="/projects">Projects</router-link>
    <router-link to="/contact">Contact</router-link>
  </nav>
  <router-view class="container" v-slot="{ Component }">
    <transition
      name="route"
      mode="out-in"
      :duration="{ enter: 600, leave: 600 }"
    >
      <component :is="Component"></component>
    </transition>
  </router-view>
</template>

<script>
import Preloader from "./components/Preloader";

export default {
  data: () => {
    return {
      firstTouch: 0,
      lastTouch: 0,
      changing: false,
      lastScroll: 0,
      showPreloader: true,
    };
  },
  methods: {
    hidePreloader() {
      setTimeout(() => {
        this.showPreloader = false;
      }, 500);
    },
    findRoute() {
      let routes = this.$router.getRoutes();

      for (var i = 0; i < routes.length; i++) {
        if (routes[i].name === this.$route.name) {
          return i;
        }
      }
      return false;
    },
    changeRoute(amount) {
      // Workaround for touchpads
      if (new Date().getTime() - this.lastScroll > 100) {
        if (this.changing == true) return;

        if (typeof this.findRoute() === "number") {
          let routes = this.$router.getRoutes();
          let id = this.findRoute();

          if (routes[amount + id]) {
            this.changing = !this.changing;
            this.$router.push({ name: routes[amount + id].name });

            setTimeout(() => {
              this.changing = !this.changing;
            }, 600);
          }
        }
      }
    },
  },
  mounted() {
    this.lastScroll = new Date().getTime();
    this.hidePreloader();
    const vue = this;

    window.addEventListener("touchstart", function (event) {
      vue.firstTouch = event.touches[0];
    });

    window.addEventListener("touchend", function () {
      if (vue.lastTouch) {
        vue.firstTouch.clientY - vue.lastTouch.clientY > 0
          ? vue.changeRoute(1)
          : vue.changeRoute(-1);
      }

      vue.firstTouch = 0;
      vue.lastTouch = 0;
    });

    window.addEventListener("touchmove", function (event) {
      var currentTouch = event.changedTouches[0];

      vue.lastTouch = currentTouch;
    });

    window.addEventListener("wheel", function (e) {
      if (e.deltaY > 0) {
        vue.changeRoute(1);
      } else {
        vue.changeRoute(-1);
      }

      vue.lastScroll = new Date().getTime();
    });
  },
  components: {
    Preloader,
  },
};
</script>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Lato:wght@400;700&display=swap");

body,
html,
#app,
.container {
  position: relative;
  overflow: hidden;

  width: 100%;
  height: 100%;

  margin: 0;
  padding: 0;

  box-sizing: border-box;

  font-family: "Lato", sans-serif;
  background-color: black;
}

.container {
  position: absolute;
  bottom: 0;
  top: 0;
  left: 0;
  right: 0;
}

nav {
  position: fixed;

  top: 0;
  left: 0;

  width: 100%;
  margin-top: 32px;

  text-align: center;

  z-index: 1;

  a {
    position: relative;

    margin: 0px 8px;

    padding: 0px 2.5%;

    text-decoration: none;
    color: rgba(0, 0, 0, 0.5);

    border-radius: 6px;

    opacity: 0.25;

    transition: 1.2s all;

    color: white;
  }

  a:before {
    position: absolute;
    content: "";

    width: 100%;
    height: 2px;

    background-color: white;
    margin-top: -8px;
  }

  a.router-link-active {
    opacity: 1;
  }
}

/* route transitions */
.route-enter-from {
  opacity: 0;
  transform: translateX(100%);
}
.route-enter-active {
  transition: all 0.6s ease-out;
}
.route-leave-to {
  opacity: 0;
  transform: translateX(-100%);
}
.route-leave-active {
  transition: all 0.6s ease-in;
}

.icon {
  margin: 0.25em;

  color: rgba(255, 255, 255);

  transition: 0.3s all;

  padding: 0.65em;
  width: 1.25em !important;
  height: 1.25em;

  font-size: 1.25em;

  border-radius: 100%;
  transform: rotateZ(15deg);

  border: 2px solid rgba(255, 255, 255, 0.5);
  background: rgba(0, 0, 0, 0.15);
}

.icon:nth-child(odd) {
  transform: rotateZ(-15deg);
}

.icon:hover {
  transform: rotateZ(-15deg);
}

.icon:nth-child(odd):hover {
  transform: rotateZ(15deg);
}

@media only screen and (min-width: 375px) {
  .icon {
    font-size: 1.5em;
    height: 1.5em;
    width: 1.5em !important;
    padding: 0.8em;
  }
}

@media only screen and (min-width: 768px) {
  .icon {
    font-size: 2em;
    height: 2em;
    width: 2em !important;
    padding: 0.75em;
  }
}

.flex {
  display: flex;
  align-items: center;
  justify-content: center;

  text-align: center;
}
</style>
