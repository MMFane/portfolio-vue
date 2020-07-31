<template>
  <div class="rtable">
    <p class="title" v-if="data.title">{{ data.title }}</p>
    <Table v-if="!smallScreen" :body="body" :headers="headers" :striped="striped" />
    <Cards v-else :body="body" :headers="headers" :striped="striped" />
  </div>
</template>
<script>
import Table from "./Table.vue";
import Cards from "./Cards.vue";
export default {
  name: "responsive-table",
  components: {
    Cards,
    Table
  },
  data() {
    return {
      body: this.data.body,
      headers: this.data.headers,
      smallScreen: window.innerWidth <= this.threshold
    };
  },
  created() {
    window.addEventListener("resize", this.handleResize);
    this.handleResize();
  },
  destroyed() {
    window.removeEventListener("resize", this.handleResize);
  },
  methods: {
    handleResize() {
      this.smallScreen = window.innerWidth <= this.threshold;
    }
  },
  props: {
    data: {
      type: Object,
      required: true
    },
    striped: {
      type: Boolean,
      default: false
    },
    threshold: {
      type: Number,
      default: 300
    }
  }
};
</script>

<style lang="css">
.rtable p {
  margin: 0;
}

.rtable .title {
  padding: 2rem 0 0.5rem 0;
  color: var(--text-color-light);
  font-size: 1.5rem;
  font-weight: bold;
  text-transform: capitalize;
}

.rtable {
  margin-bottom: 1rem;
  padding: 0 1rem;
}
</style>
