<template>
  <header id="nav">
    <p><span id="name">Samantha Yeager</span> <span id="job-title">Front End Developer</span></p>
    <nav>
      <router-link to="/">Projects</router-link> |
      <router-link to="/resume">Resume</router-link> |
      <router-link to="/about">About</router-link>
  </nav>
  </header>
</template>

<script>
export default {
  name: "Nav",
};
</script>

<style scoped>
#nav {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1rem 2rem 0 2rem;

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
