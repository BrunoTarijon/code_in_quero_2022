<template>
  <section class="pilar">
    <details class="teste">
      <summary class="summary">{{ title }}</summary>
      <Item v-for="(itemInfo, index) in dataInfo" :key="index" :item="itemInfo" :index="index"/>
    </details>
    <div class="content" v-if="showPilar"></div>
  </section>
</template>
<script>
import Item from "./Item.vue";

export default {
  components: {
    Item,
  },
  props: {
    title: String,
    dataInfo: Array
  },
  data() {
    return {
      showPilar: false,
    };
  },
  methods: {
    showPilarInfo() {
      this.showPilar = !this.showPilar;
    },
  },
};
</script>
<style scoped>
.teste {
  padding: 20px 30px;
}

.summary {
  text-align: initial;
  font-size: 20px;
  margin: 20px;
  color: #35A7E0;
  font-weight: bold;
}

.button:hover {
  background-color: #35A7E0;
  border-color: #35A7E0;
}

@media (min-width: 700px) {
  .teste {
    padding: 0 30px;
  }

  .summary {
    margin-top: 0;
  }
}
</style>