<template>
  <div id="app" class="flex items-center justify-center flex-col">
    <img alt="Vue logo" src="./assets/logo.png" />
    <section class="w-full p-4">
      <AgregarEncuesta @addSurvey="pushSurvey($event)" />
      <hr />
      <Encuesta v-for="survey in surveys" :key="survey.id" :survey="survey" />
    </section>
  </div>
</template>

<script>
import AgregarEncuesta from "./components/AgregarEncuesta";
import Encuesta from "./components/Encuesta";

export default {
  name: "App",
  components: {
    AgregarEncuesta,
    Encuesta
  },
  data() {
    return {
      surveys: []
    };
  },
  methods: {
    pushSurvey(survey) {
      this.surveys.push(survey);
    }
  }
};
</script>
