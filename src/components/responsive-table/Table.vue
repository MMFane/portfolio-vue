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
  background-color: var(--table-color);
  box-shadow: 0 3px 10px var(--shadow-color);
}
.rtable rtable-table {
  margin: 0 auto 1rem auto;
}
.rtable-table thead {
  box-shadow: 0 0 5px var(--shadow-color);
}
.rtable-table th,
.rtable-table td {
  border-bottom: 1px solid var(--border-color);
  padding: 1rem 2rem;
  min-width: 50px;
}
.rtable-table th {
  text-align: left;
}
.rtable-table.striped tr:nth-of-type(even) {
  background-color: var(--table-color-dark);
}
</style>
