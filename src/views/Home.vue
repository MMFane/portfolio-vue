<template>
  <main id="router-view">
    <h1 id="title">Projects</h1>
    <transition name="fade" mode="out-in">
      <section v-if="!projectSelected" key="project-list">
        <ul id="thumbnails">
          <li v-for="(project, index) in projects" :key="index">
            <ProjectThumb
              :id="index"
              :img="project.img"
              :name="project.name"
              @changeProject="changeProject"
            />
          </li>
        </ul>
      </section>
      <article v-else id="project" key="project-view">
        <button @click="clearSelected" id="back-btn">Back</button>
        <ViewFillableVectorGraphic v-if="whichProjectSelected === 'vector'" />
        <ViewFormUX v-if="whichProjectSelected === 'form'" />
        <ViewResponsiveTable v-if="whichProjectSelected === 'table'" />
      </article>
    </transition>
  </main>
</template>

<script>
import ProjectThumb from "@/components/ProjectThumbnail.vue";
import ViewFillableVectorGraphic from "@/views/projects/ViewFillableVectorGraphic.vue"
import ViewFormUX from "@/views/projects/ViewFormUX.vue"
import ViewResponsiveTable from "@/views/projects/ViewResponsiveTable.vue";
import Projects from "@/assets/projects.json";

export default {
  name: "Home",
  components: {
    ProjectThumb,
    ViewFillableVectorGraphic,
    ViewFormUX,
    ViewResponsiveTable
  },
  computed: {
    projectSelected() {
      return this.selectedProject !== null;
    },
    whichProjectSelected() {
      return this.projects[this.selectedProject].shortname
    }
  },
  data() {
    return {
      projects: Projects,
      selectedProject: null
    };
  },
  methods: {
    changeProject(id) {
      console.log(`Home Changing Project to ${id}`);
      this.selectedProject = id;
    },
    clearSelected() {
      this.selectedProject = null;
    }
  }
};
</script>

<style scoped>
ul {
  list-style: none;
}

#back-btn {
  align-self: center;
  width: auto;
}

#project {
  display: flex;
  flex-direction: column;
  margin: 0 2rem;
}

#router-view #title {
  align-self: center;
}

#thumbnails {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}

.fade-enter-active,
.fade-leave-active {
  transition: all 0.15s ease-in;
}

.fade-enter,
.fade-leave-to {
  opacity: 0;
  transform: translateY(10%);
}
</style>
