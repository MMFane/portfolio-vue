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
#app {
  width: 100%;
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-content: center;
  font-family: Roboto, Arial, sans-serif;
}

#main-content {
  margin: 1rem 0;
  padding: 1rem 0;
  border: 1px solid black;
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
