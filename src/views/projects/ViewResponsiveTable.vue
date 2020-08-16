<template>
  <section id="project">
    <h2>Responsive Table</h2>
    <h3>Concept</h3>
    <p>Tables don't work so well on small screens, so this one changes to a card style display for each table row on screens smaller than a set threshold. This way, related data remains visually connected, but also flexible</p>
    <h3>Properties</h3>
    <p>
      <ul>
        <li><b>Data</b> - JSON Object with the properties
          <ul>
            <li><b>Title</b> - Title for the entire table</li>
            <li><b>Headers</b> - Headers for each table column</li>
            <li><b>Body</b> - Array of arrays for each row</li>
          </ul>
         </li>
        <li><b>Striped</b> - Boolean to set row stripes. Default false.</li>
        <li><b>Threshold</b> - Integer to set screen size at which the table changes to cards. Default 300.</li>
      </ul>
    </p>
    <h3>Play with the table below</h3>
    <form>
      <input type="checkbox" name="striped" v-model="striped"/>
      <label for="striped">Striped?</label>
      <label for="threshold">Threshold</label>
      <input name="threshold" v-model.number="threshold"/>
    </form>
    <ResponsiveTable :data="data" :threshold="threshold" :striped="striped" />
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
      },
      striped: true,
      threshold: 450,
    };
  }
};
</script>

<style>

table {
  background-color: var(--background-light);
  border: 1px solid var(--background-med);
}

td {
  border: 1px solid var(--shadow-med);
}

</style>
