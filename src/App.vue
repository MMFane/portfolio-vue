<template>
  <main id="app">
    <Nav />
    <router-view id="main-content" />
    <Footer />
  </main>
</template>

<script>
import Footer from "@/components/Footer.vue";
import Nav from "@/components/Nav.vue";

export default {
  name: "App",
  components: {
    Footer,
    Nav,
  },
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Nunito');
:root {
  --dialog-light: #fcf7ff;
  --shadow: rgba(37, 0, 59, 0.05);
  --text: rgb(51, 0, 51);
  --text-deemph: rgba(51, 0, 51, 0.75);
  --link: #d96d0f;
  --link-hover: #9c3600;
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

a {
  color: var(--link);
  text-decoration: none;
  border-bottom: 1px dashed var(--link);
}

a:hover {
  color: var(--link-hover);
  padding-bottom: 0.25rem;

}

#main-content {
  margin: 1rem 0;
  padding: 1rem 0;
  flex-grow: 1;
  display: flex;
  flex-direction: column;
  align-items: center;
}

button {
  border: none;
  color: white;
  background-color: purple;
  padding: 0.5rem 1rem;
}
</style>
