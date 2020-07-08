<template>
  <section id="router-view">
    <h1 id="title">Projects</h1>
    <transition name="fade" mode="out-in">
      <ul id="thumbnails" v-if="!projectSelected" key="thumnail-list">
        <li v-for="(project, index) in projects" :key="index">
          <ProjectThumb
            :id="index"
            :img="project.img"
            :name="project.name"
            @changeProject="changeProject"
          />
        </li>
      </ul>
      <article id="project" v-else key="project-view">
        <button @click="clearSelected">Back</button>
        <section>
          // TO DO add project view by index
        </section>
      </article>
    </transition>
  </section>
</template>

<script>
import ProjectThumb from "@/components/ProjectThumbnail.vue";
import Projects from "@/assets/projects.json";

export default {
  name: "Home",
  components: {
    ProjectThumb,
  },
  computed: {
    projectSelected() {
      return this.selectedProject !== null;
    },
  },
  data() {
    return {
      projects: Projects,
      selectedProject: null,
    };
  },
  methods: {
    changeProject(id) {
      console.log(`Home Changing Project to ${id}`);
      this.selectedProject = id;
    },
    clearSelected() {
      this.selectedProject = null;
    },
  },
};
</script>

<style scoped>
ul {
  list-style: none;
}

#router-view #title {
  align-self: center;
}

#thumbnails {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}

#project {
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 100%;
  height: 500px;
}

.fade-enter-active,
.fade-leave-active {
  transition: all 0.3s ease;
}

.fade-enter,
.fade-leave-to {
  opacity: 0;
  transform: translateY(100%);
}
</style>
