<template>
  <section class="guide">
    <div class="card">
      <p><b>Bruno</b></p>
      <p>{{ this.infoGuide.data[0] }}</p>
      <p>/artigo-sobre-git</p>
    </div>
    <div class="card">
      <p><b>Gustavo</b></p>
      <p>{{ this.infoGuide.data[0] }}</p>
      <p>/curso-de-banco-de-dados</p>
    </div>
    <div class="card">
      <p><b>Michael</b></p>
      <p>{{ this.infoGuide.data[0] }}</p>
    </div>
  </section>
</template>
<script>
import axios from 'axios'
export default {
  props:{
    itemGuide: Object
  },
  data(){
    return {
      infoGuide: null
    }
  },
  async mounted() {
    await axios
      .get('http://localhost:3000/api/v1/materials/assunto/?title=Entende os conceitos básicos de uma API')
      .then((response) => (this.infoGuide = response));
  },
  method: {
    filterItemGuide() {

    }
  }
};
</script>
<style scoped>
.card {
  padding: 20px;
  margin-top: 10px;
}
</style>