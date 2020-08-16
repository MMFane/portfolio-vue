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

.rtable-cards p {
  background-color: unset;
  border-radius: 0;
  box-shadow: none;
}

.rtable-cards .card {
  flex-grow: 1;
  position: relative;
  margin: 0.5rem;
  background-color: var(--background-light);
}

.rtable-cards .row {
  display: flex;
  border-bottom: 1px solid var(--shadow-med);
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
  box-shadow: 3px 0 7px var(--shadow-med);
}

.rtable-cards.striped .card .row:nth-of-type(odd) p.data {
  background-color: var(--background-med);
}

.rtable-cards .row .data,
.rtable-cards .row .header {
  flex-basis: 50%;
  flex-grow: 1;
}
</style>
