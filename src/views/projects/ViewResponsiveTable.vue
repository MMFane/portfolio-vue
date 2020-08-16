<template>
  <section id="project">
    <h2>Responsive Table</h2>
    <h3>Concept</h3>
    <p>Tables don't work so well on small screens, so this one changes to a card style display for each table row on screens smaller than a set threshold. This way, related data remains visually connected, but also flexible</p>
    <h3>Properties</h3>
    <ul>
      <li>Data</li>
      <li>Striped</li>
      <li>Threshold</li>
    </ul>
    <ResponsiveTable :data="data" :threshold="450" :striped="true" />
    <h2>Dogs (Normal Table)</h2>
    <table>
      <thead>
        <th v-for="(header, index) in data.headers" :key="`header-${index}`">{{ header }}</th>
        <tr v-for="(row, index) in data.body" :key="`row-${index}`">
          <td v-for="(entry, index) in row" :key="`data-${index}`">{{ entry }}</td>
        </tr>
      </thead>
    </table>
  </section>
</template>

<script>
import ResponsiveTable from "@/components/responsive-table/ResponsiveTable.vue";
export default {
  components: {
    ResponsiveTable
  },
  data() {
    return {
      data: {
        title: "Dogs (Responsive Table)",
        headers: ["Name", "Breed", "Favorite Toy"],
        body: [
          ["Frank Frank", "Golden Retriever", "Sprinklers"],
          ["Tucker", "Bichon Frise", "His brother"],
          ["Champ", "Bichon Frise", "Squirrels"],
          ["Django", "Border Collie Mix", "Frisbee"],
          ["Frou Frou", "Havanese", "Left pink sock"],
          ["Miles", "Pitbull Mix", "A ragged chew toy"]
        ]
      }
    };
  }
};
</script>

<style>
:root {
  --table-color-dark: lightblue;
}

thead {
  background-color: cyan;
}

</style>
