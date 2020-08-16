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
  padding: 1rem 2rem 0 2rem;
  box-shadow: 0 10px 10px var(--shadow);
}

 #name {
   font-size: 1.5rem;
  font-weight: 700;
}

#job-title {
  font-size: 1.25rem;
  color: var(--text-deemph);
  font-style: italic;
}
</style>
