<template>
  <div :class="{ 'rtable-cards': true, striped: striped }">
    <div class="card" v-for="(row, index) in body" :key="`card-${index}`">
      <div class="head-shadow"></div>
      <div
        class="row"
        v-for="(header, index) in headers"
        :key="`card-${index}-row-${index}`"
      >
        <p class="header">{{ header }}</p>
        <p class="data">{{ row[index] }}</p>
      </div>
    </div>
  </div>
</template>
z
<script>
export default {
  name: "r-cards",
  props: {
    body: Array,
    headers: Array,
    striped: Boolean,
  },
};
</script>
<style>
.rtable-cards {
  display: flex;
  flex-wrap: wrap;
}
.rtable-cards.striped .card .row:nth-of-type(even) {
  background-color: var(--table-color-dark);
}
.rtable-cards .card {
  display: flex;
  flex-direction: column;
  flex-grow: 1;
  position: relative;
  width: 43%;
  min-width: 200px;
  margin: 0.5rem;
  background-color: var(--table-color);
}
.rtable-cards .row {
  display: flex;
  flex-grow: 1;
  position: relative;
}
.rtable-cards .row:last-child {
  border-bottom: none;
}
.rtable-cards .row * {
  padding: 0.5rem;
}
.rtable-cards .row .header {
  font-weight: bold;
}
.rtable-cards .head-shadow {
  position: absolute;
  width: 50%;
  height: 100%;
  box-shadow: 0 0 5px var(--shadow-color);
}
.rtable-cards .row .data,
.rtable-cards .row .header {
  flex-basis: 50%;
  flex-grow: 1;
}
</style>
