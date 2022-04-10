<template>
  <div id="app">
    <section class="profile">
      <header></header>
      <div class="info-profile">
        <img alt="Imagem de Perfil" src="./assets/michael.jpeg" />
        <p>
          Nome: <b>{{ info.data.name }}</b>
        </p>
        <p>Contato: <b>{{ info.data.contact }}</b></p>
        <p>Link github: <b>{{ info.data.link }}</b></p>
      </div>
      <div class="content">
        <PilarCard title="Fundamentos" :dataInfo="competenceFundamentals"/>
        <PilarCard title="Programação" :dataInfo="competenceProgramming"/>
        <PilarCard title="Produto" :dataInfo="competencePeople" />
      </div>
    </section>
  </div>
</template>

<script>
import PilarCard from "./components/PilarCard.vue";
import axios from "axios";

export default {
  name: "App",
  components: {
    PilarCard,
  },
  data: function () {
    return {
      info: null,
      description: null,
      competence: null,
      competenceFundamentals: null,
      competenceProgramming: null,
      competencePeople: null

    };
  },
  async mounted() {
    await axios
      .get("http://localhost:3000/api/v1/users/4")
      .then((response) => (this.info = response));
     await axios
      .get("http://localhost:3000/api/v1/competences/4")
      .then((response) => (this.competence = response));
    //    this.competenceFundamentals = this.competence.data.filter(e => {
    //     e.group == 'Fundamentos' })
    this.getCompetence()
  },
  methods: {
    async filterGroupFundamentals(group){
     this.competenceFundamentals =  await group.filter( e => {
        e.group == 'Fundamentos'
      })
    },
    async getCompetence() {
     try {
        const { data } = await axios.get('http://localhost:3000/api/v1/competences/4');
        this.competenceFundamentals = data.filter( e => e.group == 'Fundamentos' )
        this.competenceProgramming = data.filter( e => e.group == 'Programação' )
        this.competencePeople = data.filter( e => e.group == 'Pessoas' )
      } catch (error) {
        console.error(error);
      }
    }
  }
};
</script>

<style >
ul li {
  list-style: none;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

#app h3 {
  text-align: center;
  font-weight: bold;
  margin-top: 25px;
}

.header {
  display: flex;
  justify-content: center;
  align-items: center;
}

.header input {
  margin-left: 10px;
}

.info-profile p {
  text-align: initial;
  margin-top: 20px;
  margin-left: 25px;
}

.general {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.competencia {
  display: flex;
  flex-direction: column;
}

.profile img {
  width: 300px;
  margin-left: 20px;
  margin: 0 auto;
  border-radius: 50%;
}

.profile {
  display: flex;
  flex-direction: column;
  height: 100vh;
}

@media (min-width: 700px) {
  .profile {
    flex-direction: inherit;
    margin-left: 30px;
  }

  .content {
    display: flex;
    justify-content: center;
  }
}
</style>
