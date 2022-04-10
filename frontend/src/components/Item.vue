<template>
  <section class="item">
    <div class="card">
      <div class="title">
        <h4 @click="showCompetenceInformation">
          {{ this.item.title }}
        </h4>
      </div>
      <div class="content" v-if="showCompetence">
        <hr />
        <p>
          {{ this.item.description }}
        </p>
        <h5>Evidência</h5>
        <b-form-textarea
          name="evidence"
          id="evidence"
          cols="40"
          rows="2"
        ></b-form-textarea>
        <h5>Guia</h5>
        <b-form-textarea
          name="guia"
          id="guia"
          cols="40"
          rows="2"
        ></b-form-textarea>
        <div>
          <b-button @click="showModal"  variant="outline-primary">Mostrar Guias</b-button>
          <b-modal ref="myModal" title="Guia">
            <GuideCard :itemGuide="item" />
          </b-modal>
        </div>
      </div>
    </div>
  </section>
</template>
<script>
import GuideCard from "./GuideCard.vue";
export default {
  components: {
    GuideCard,
  },
  props: {
    item: Object,
    index: Number
  },
  data: function () {
    return {
      showEvidence: false,
      showGuide: false,
      showCompetence: false,
    };
  },
  methods: {
    showMoreEvidence() {
      this.showEvidence = !this.showEvidence;
    },
    showMoreGuide() {
      this.showGuide = !this.showGuide;
    },
    showCompetenceInformation() {
      this.showCompetence = !this.showCompetence;
    },
    showModal(){
      this.$refs['myModal'].show();
    }
  },
};
</script>
<style scoped>
h1 {
  display: flex;
  justify-content: center;
  flex-direction: column;
}

h5 {
  margin-top: 10px;
}

.title {
  display: flex;
}

.item {
  display: flex;
  justify-content: center;
}

.item-list {
  padding: 20px 0;
}
.item-list ul {
  padding: 0;
}
.item-list ul li {
  padding: 0;
}

.item button {
  margin-top: 10px;
}
.card {
  border-radius: 5px;
  box-shadow: 7px 7px 13px 0px rgba(50, 50, 50, 0.22);
  padding: 30px;
  margin: 20px;
  width: 400px;
  transition: all 0.3s ease-out;
  text-align: initial;
}

.card:hover {
  transform: translateY(-5px);
  cursor: pointer;
}

.card p {
  color: #a3a5ae;
  font-size: 16px;
}

@media (min-width: 600px) {
  .content {
    display: flex;
    flex-direction: column;
  }
}
</style>