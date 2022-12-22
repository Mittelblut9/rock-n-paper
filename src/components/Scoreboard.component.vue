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
    getScore() {
      return this.player_score
    },
    updatePlayerScore(type) { 
      const score = parseInt(this.getScore());
      const newScore = (type === 'You win') ? score + 1 : (type === 'You lose') ? score - 1 : score;
      this.player_score = (newScore < 0) ? 0 : newScore;
    },
    savePlayerScore() {
      localStorage.setItem('player_score', this.player_score);
    }
  },
  watch: {
    player_score() {
      this.savePlayerScore();
    }
  },
  mounted() {

    this.player_score = localStorage.getItem('player_score') || 0;

    this.emitter.on("updatePlayerScore", status => {
      this.updatePlayerScore(status);
    });
  }
}
</script>

<style scoped>
@import url('@/assets/css/Scoreboard/style.css');
</style>
