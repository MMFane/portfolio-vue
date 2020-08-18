<template>
  <main id="app">
    <Header />
    <router-view id="main-content" />
    <Footer />
  </main>
</template>

<script>
import Footer from "@/components/Footer.vue";
import Header from "@/components/Header.vue";

export default {
  name: "App",
  components: {
    Footer,
    Header,
  },
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Nunito');
:root {
  --background-light: #fcf7ff;
  --background-med: #c1adcc;
  --background-dark: #7c5f8c;
  --shadow: rgba(37, 0, 59, 0.05);
  --shadow-med: rgba(37, 0, 59, 0.1);
  --text: rgb(51, 0, 51);
  --text-deemph: rgba(51, 0, 51, 0.75);
  --link: #d96d0f;
  --link-hover: #9c3600;
}

a {
  color: var(--link);
  text-decoration: none;
  border-bottom: 1px dashed var(--link);
}

a:hover {
  color: var(--link-hover);
  padding-bottom: 0.25rem;
}

button {
  border: none;
  color: white;
  background-color: purple;
  padding: 0.5rem 1rem;
}

h1 {
  margin: 0 0 2rem 0;
}

h2, p {
  margin: 0 0 1.2rem 0;
}

h3 {
  color: var(--text-deemph);
  margin: 0 0 0.8rem 0;
}

p {
  background-color: var(--background-light);
  padding: 1rem;
  border-radius: 10px;
  box-shadow: inset 0 5px 10px var(--shadow);
}

ul {
  margin: 0;
}

#app {
  width: 100%;
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-content: center;
  font-family: Nunito, Arial, sans-serif;
  color: var(--text);
}

#main-content {
  margin: 1rem 0;
  padding: 1rem 0;
  flex-grow: 1;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.mb-1 {
  margin-bottom: 1rem;
}

</style>
