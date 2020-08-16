<template>
  <header>
    <p><span id="name">Samantha Yeager</span> <span id="job-title">Front End Developer</span></p>
    <nav>
      <router-link to="/">Projects</router-link> |
      <router-link to="/resume">Resume</router-link> |
      <router-link to="/about">About</router-link>
      <font-awesome-icon icon="bars" id="nav-collapse" @click="toggleNav" v-show="smallScreen"/>
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
