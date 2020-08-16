<template>
  <header>
    <div id="me">
      <div id="name-title">
        <span id="name">Samantha Yeager </span>
        <span id="job-title">Front End Developer</span>
      </div>
      <font-awesome-icon icon="bars" id="nav-collapse" @click="toggleNav" v-show="smallScreen"/>
    </div>
    <nav v-show="!smallScreen || isNavOpen">
      <router-link class="router-link" to="/">Projects</router-link><span class="nav-divider"> |</span>
      <router-link class="router-link" to="/resume">Resume</router-link><span class="nav-divider"> |</span>
      <router-link class="router-link" to="/about">About</router-link>
    </nav>
  </header>
</template>

<script>
import { library } from '@fortawesome/fontawesome-svg-core'
import { faBars } from '@fortawesome/free-solid-svg-icons'
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome'

library.add(faBars)

export default {
  name: "Nav",
  components: {
    FontAwesomeIcon
  },
  data() {
    return {
      isNavOpen: false,
      screenBreakpoint: 650,
      smallScreen: window.innerWidth < this.screenBreakpoint
    }
  },
  methods: {
    resizeWindow() {
      this.windowWidth = window.innerWidth;
      this.smallScreen = window.innerWidth < this.screenBreakpoint;
    },
    toggleNav() {
      this.isNavOpen = !this.isNavOpen;
    }
  },
  created() {
    window.addEventListener("resize", this.resizeWindow);
    this.resizeWindow();
  },
  destroyed() {
    window.removeEventListener("resize", this.resizeWindow)
  },
};
</script>

<style scoped>
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1rem 1rem 0 1rem;
  box-shadow: 0 10px 10px var(--shadow);
}

#me {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

#name {
  font-size: 1.5rem;
  font-weight: 700;
}

#nav-collapse {
  display: none;
}

#job-title {
  font-size: 1.25rem;
  color: var(--text-deemph);
  font-style: italic;
}

@media (max-width: 650px) {
  header {
    flex-direction: column;
  }

  nav {
    display: flex;
    flex-direction: column;
  }

  a.router-link {
    display: block;
    width: 100vh;
    background-color: var(--shadow);
    text-align: center;
  }

  a.router-link:first-of-type {
    border-top: 1px solid var(--shadow);
  }

  #me {
    width: 100%;
  }

  #me #name-title {
    display: flex;
    flex-direction: column;
  }

  #nav-collapse {
    display: block;
    justify-self: right;
  }

  .nav-divider {
    display: none;
  }
}

</style>
