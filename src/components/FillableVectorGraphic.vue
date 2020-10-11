<template>
  <article>
    <p>Sam is filled to {{ displayPercent }}%</p>
    <div id="svg">
      <Colors :alt="`Sam is filled to ${ displayPercent }`"/>
      <svg id="mask" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 408 512" :style="maskCSS">
        <rect width="408" height="512" :fill="backgroundColor"/>
      </svg>
      <Lines alt=""/>
    </div>
  </article>
</template>

<script>
import Lines from "@/assets/sam-lines.svg";
import Colors from "@/assets/sam-colors.svg";
export default {
  name: "FillableVectorGraphic",
  components: {
    Colors,
    Lines,
  },
  computed: {
    displayPercent() {
      return this.round(this.roundedPercent * 100, 2)
    },
    filteredPercent() {
      if (this.percentage < 0) return 0
      else if (this.percentage > 1) return 1
      else return this.percentage
    },
    maskCSS() {
      return `transform: scale(1, ${ 1 - this.roundedPercent }`
    },
    roundedPercent() {
      return this.round(this.filteredPercent, 2)
    }
  },
  data() {
    return {
      backgroundColor: '#fff',
      percentage: 0.7,
    }
  },
  methods: {
    round(value, places) {
      return Number(Math.round(`${ value }e${ places }`) + `e-${ places }`)
    }
  }
}
</script>

<style>
#svg {
  position: relative;
  width: 500px;
}

#colors,
#lines,
#mask {
  width: 100%;
  position: absolute;
  top: 10%;
  left: 0;
}

#mask {
  transform-origin: top;
}
</style>