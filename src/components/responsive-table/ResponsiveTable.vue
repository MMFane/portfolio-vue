<template>
  <div class="rtable">
    <DynamicHeader v-if="data.title" :level="headerLevel">{{ data.title }}</DynamicHeader>
    <Table v-if="!smallScreen" :body="body" :headers="headers" :striped="striped" />
    <Cards v-else :body="body" :headers="headers" :striped="striped" />
  </div>
</template>
<script>
import Table from "./Table.vue";
import Cards from "./Cards.vue";
import DynamicHeader from "../utility/DynamicHeader.vue";

export default {
  name: "responsive-table",
  components: {
    Cards,
    DynamicHeader,
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
    headerLevel: {
      type: Number,
      default: 2
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
  display: flex;
  flex-direction: column;
  align-items: center;
}

.rtable p {
  margin: 0;
}
</style>
