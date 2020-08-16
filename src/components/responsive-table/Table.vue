<template>
  <table :class="{ 'rtable-table': true, striped: striped }">
    <thead>
      <th v-for="(header, index) in headers" :key="`header-${index}`">
        {{ header }}
      </th>
    </thead>
    <tbody>
      <tr v-for="(row, index) in body" :key="`row-${index}`">
        <td v-for="(info, index) in row" :key="`row${index}-info-${index}`">
          {{ info }}
        </td>
      </tr>
    </tbody>
  </table>
</template>
<script>
export default {
  name: "r-table",
  props: {
    body: Array,
    headers: Array,
    striped: Boolean,
  },
};
</script>
<style>
.rtable-table {
  border-collapse: collapse;
  box-shadow: 0 5px 15px var(--shadow-med);
  margin: 0 auto 1rem auto;
}

.rtable-table tr {
  box-shadow: inset 0 0 5px var(--shadow);
}

.rtable-table tr:first-of-type {
  box-shadow: inset 0 7px 5px var(--shadow-med);
}

.rtable-table th,
.rtable-table td {
  padding: 1rem 2rem;
  min-width: 50px;
}

.rtable-table th {
  text-align: left;
}

.rtable-table.striped tr:nth-of-type(odd) {
  background-color: var(--background-med);
}
</style>
