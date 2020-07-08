<template>
  <section
    class="project"
    :style="{ backgroundImage: `url(${img})` }"
    @click="changeProject"
  >
    <h2 class="title">{{ name }}</h2>
  </section>
</template>

<script>
export default {
  name: "ProjectThumb",
  methods: {
    changeProject() {
      this.$emit("changeProject", this.id);
    },
  },
  props: {
    id: {
      type: Number,
      required: true,
    },
    img: {
      type: String,
      default:
        "https://images.unsplash.com/photo-1499951360447-b19be8fe80f5?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1500&q=80",
    },
    name: {
      type: String,
      default: "Project",
    },
  },
};
</script>

<style>
.project {
  width: 300px;
  height: 300px;
  background-position: center;
  background-size: cover;
  display: flex;
  justify-content: center;
  align-items: flex-end;
  padding: 1rem;
  margin: 0 2rem 2rem 0;
}

.project .title {
  color: white;
  font-weight: bold;
  font-size: 2rem;
  background-color: rgba(0, 0, 0, 0.25);
  margin: 0;
  padding: 0.5rem 1rem;
}
</style>
