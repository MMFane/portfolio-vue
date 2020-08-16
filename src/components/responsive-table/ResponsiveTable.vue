<template>
  <div class="rtable">
    <h2 v-if="data.title">{{ data.title }}</h2>
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
.rtable {
  margin-bottom: 2rem;
}

.rtable p {
  margin: 0;
}
</style>
