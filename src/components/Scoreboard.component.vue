<template>
  <div class="scoreboard">
    <h1>
      <p>Rock</p>
      <p>Paper</p>
      <p>Scissors</p>
    </h1>
    <div class="score">
      <div class="player_score">
        <p>Player</p>
        <p>{{ player_score }}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Scoreboard',
  data() {
    return {
      player_score: 0
    }
  },
  methods: {
    updatePlayerScore(player_score) {
      this.player_score = player_score
    },
  }
}
</script>

<style scoped>
@import url('@/assets/css/Scoreboard/style.css');
</style>
