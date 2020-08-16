<template>
  <footer>
    <a href="mailto:sam.erin.yeager@gmail.com" target="_blank"
      >sam.erin.yeager@gmail.com</a
    >
    <a href="tel:740-591-7429">(740) 591-7429</a>
    <a href="">LinkedIn</a>
  </footer>
</template>

<script>
export default {
  name: "Footer",
};
</script>

<style>
footer {
  width: 100%;
  height: 50px;
  line-height: 50px;
  display: flex;
  justify-content: space-around;
  box-shadow: 0 -10px 10px var(--shadow);
}
</style>
