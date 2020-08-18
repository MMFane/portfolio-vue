<template>
  <section id="project">
    <section>
      <h2>Responsive Table</h2>
      <h3>Concept</h3>
      <p>Tables with more than two or three rows or with long sentences in their data don't work so well on small screens. To address this, on screens smaller than a set threshold this component changes to a card-style display. Related data remains visually connected, but can be much thinner in the horizontal axis, making it flexible for mobile-responsive sites.</p>
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
    </section>
    <section>
      <h2>Examples</h2>
      <h3>Try changing the table properties</h3>
      <form id="table-form" class="mb-1">
        <label for="striped">
          <input type="checkbox" name="striped" v-model="striped"/>
          Striped?
        </label>
        <label for="threshold">Threshold <font-awesome-icon icon="info-circle" @hover="showThresholdTip = true" @click="showThresholdTip = true" />
          <input name="threshold" type="text" v-model.number="threshold"/>
        </label>
      </form>
      <ResponsiveTable :data="data" :threshold="threshold" :striped="striped" />
      
      <h3>Non-Responsive Table</h3>
      <h4>Dogs</h4>
      <table>
        <thead>
          <th v-for="(header, index) in data.headers" :key="`header-${index}`">{{ header }}</th>
        </thead>
        <tbody>
          <tr v-for="(row, index) in data.body" :key="`row-${index}`">
            <td v-for="(entry, index) in row" :key="`data-${index}`">{{ entry }}</td>
          </tr>
        </tbody>
      </table>
    </section>
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
        title: "Responsive Table",
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
      showThresholdTip: false,
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

#table-form {
  display: flex;
  flex-wrap: wrap;
}

#table-form label {
  margin-right: 1rem;
}

#table-form input[type="text"] {
  margin-left: 0.5rem;
}

</style>
