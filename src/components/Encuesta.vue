<template>
  <div class="encuesta">
    <div class="encuesta__pregunta">
      {{ survey.question }}
    </div>
    <div class="encuesta__respuestas">
      <ul>
        <li
          v-for="option in survey.options"
          :key="option.id"
          @click="addVote(option)"
        >
          <span class="encuesta__respuestas--text">
            {{ option.text }}
          </span>
          <span
            class="encuesta__respuestas--progress"
            :style="`width: ${getPercentage(option.votes, totalVotes)}%`"
          >
            <span>{{ getPercentage(option.votes, totalVotes) }}%</span>
          </span>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  props: ["survey"],
  computed: {
    totalVotes() {
      return this.survey.options.reduce((totalVotes, { votes }) => {
        return totalVotes + votes;
      }, 0);
    }
  },
  methods: {
    getPercentage(value, total) {
      return Math.round((value * 100) / total);
    },
    addVote(option) {
      option.votes += 1;
    }
  }
};
</script>

<style src="@/assets/components/Encuesta.scss" lang="scss" scoped></style>
