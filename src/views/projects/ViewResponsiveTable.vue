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
      <h3>Responsive Table</h3>
      <ResponsiveTable :data="data" :header-level="4" :threshold="threshold" :striped="striped" />
      
      <h3>Non-Responsive Table</h3>
      <div id="non-resp-table">
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
      </div>
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
        title: "Dogs",
        headers: ["Name", "Breed", "Age", "Favorite Toy"],
        body: [
          ["Frank Frank", "Golden Retriever", "1", "He likes romping through sprinklers and biting the water."],
          ["Tucker", "Bichon Frise", "16", "His brother. They fight and sneeze at each other constantly, but it's all in good fun."],
          ["Champ", "Bichon Frise", "13", "Squirrels. Or perhaps he's just conditioned to the sound of your voice. \"Banana! Is there a banana outside the window, boy?\""],
          ["Django", "Border Collie Mix", "6mo", "Frisbee. He chased it like it was nobody's business."],
          ["Frou Frou", "Havanese", "8", "Left pink sock. Maybe the right ones smell wrong."],
          ["Miles", "Pitbull Mix", "4", "A ragged chew toy. It's the first one we ever gave him and the only one he'll touch."]
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

#non-resp-table {
  display: flex;
  flex-direction: column;
  align-items: center;
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
