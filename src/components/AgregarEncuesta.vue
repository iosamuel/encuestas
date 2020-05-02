<template>
  <div class="agregar">
    <div class="agregar__encuesta">
      <input
        type="text"
        placeholder="Agregar encuesta..."
        v-model="question"
        @focus="add = true"
      />
      <button @click="addSurvey()">Agregar</button>
    </div>
    <div class="agregar__opciones" v-show="add">
      <template v-for="option in options">
        <input
          type="text"
          :placeholder="`Opcion ${option.id + 1}`"
          v-model="option.text"
          :key="option.id"
        />
      </template>
      <button @click="addOption()">Agregar Opcion</button>
    </div>
  </div>
</template>

<script>
const defaultOption = () => [
  { id: 0, text: "", votes: 0 },
  { id: 1, text: "", votes: 0 }
];

export default {
  data() {
    return {
      add: false,
      question: "",
      options: defaultOption()
    };
  },
  methods: {
    addOption() {
      this.options.push({
        id: this.options.length,
        text: "",
        votes: 0
      });
    },
    addSurvey() {
      this.$emit("addSurvey", {
        id: Math.random().toString(),
        question: this.question,
        options: this.options
      });

      this.question = "";
      this.options = defaultOption();
    }
  }
};
</script>

<style
  src="@/assets/components/AgregarEncuesta.scss"
  lang="scss"
  scoped
></style>
