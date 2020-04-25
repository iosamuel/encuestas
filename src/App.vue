<template>
  <div id="app" class="flex items-center justify-center flex-col">
    <img alt="Vue logo" src="./assets/logo.png" />
    <section class="w-full p-4">
      <div class="agregar">
        <div class="agregar__encuesta">
          <input
            type="text"
            placeholder="Agregar encuesta..."
            @focus="add = true"
          />
          <button>Agregar</button>
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
      <hr />
      <div class="encuesta">
        <div class="encuesta__pregunta">
          Capa que mas utilizas de Vue?
        </div>
        <div class="encuesta__respuestas">
          <ul>
            <li>
              <span class="encuesta__respuestas--text">
                Declarative Rendering
              </span>
              <span class="encuesta__respuestas--progress" style="width: 50%">
                <span>50%</span>
              </span>
            </li>
            <li>
              <span class="encuesta__respuestas--text">
                Declarative Rendering
              </span>
              <span class="encuesta__respuestas--progress" style="width: 25%">
                <span>25%</span>
              </span>
            </li>
            <li>
              <span class="encuesta__respuestas--text">
                Declarative Rendering
              </span>
              <span class="encuesta__respuestas--progress" style="width: 10%">
                <span>10%</span>
              </span>
            </li>
          </ul>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  name: "App",
  components: {},
  data() {
    return {
      add: false,
      options: [{ id: 0, text: "" }]
    };
  },
  methods: {
    addOption() {
      this.options.push({
        id: this.options.length,
        text: ""
      });
    }
  }
};
</script>

<style lang="scss"></style>
