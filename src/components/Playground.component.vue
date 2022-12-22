<template>
  <div class="playground">
    <div class="player_select" v-if="!player_select && !pc_select">
      <div class="player_select_options">
        <div class="player_select_option rock" id="rock" @click="play('rock')">
          <img src="@/assets/img/icon-rock.svg" alt="rock">
        </div>
        <div class="player_select_option paper" id="paper" @click="play('paper')">
          <img src="@/assets/img/icon-paper.svg" alt="paper">
        </div>
        <div class="player_select_option scissors" id="scissors" @click="play('scissors')">
          <img src="@/assets/img/icon-scissors.svg" alt="scissors">
        </div>

      </div>
    </div>

    <div class="result" v-else>
      <div class="result_options">
        <div>
          <h2>You picked</h2>
          <div class="player_select_option" :class="player_select">
            <img :src="require('@/assets/img/icon-' + player_select + '.svg')" alt="player">
          </div>
        </div>

        <div class="result_status">
          <h1>{{ status }}</h1>
          <button @click="player_select = null; pc_select = null">Play again</button>
        </div>

        <div>
          <h2>The house picked</h2>
          <div class="player_select_option pc" :class="pc_select">
            <img :src="require('@/assets/img/icon-' + pc_select + '.svg')" alt="pc">
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Playground',
  data() {
    return {
      player_select: null,
      pc_select: null,
      status: null
    }
  },
  methods: {
    play(player_select) {
      this.player_select = player_select
      this.status = this.compare()
      this.emitter.emit("updatePlayerScore", this.status);
    },
    compare() {
      const player_select = this.player_select
      const pc_select = this.pc_player()

      if (player_select === pc_select) {
        return 'It\'s a tie'
      } else if (player_select === 'rock' && pc_select === 'scissors') {
        return 'You win'
      } else if (player_select === 'paper' && pc_select === 'rock') {
        return 'You win'
      } else if (player_select === 'scissors' && pc_select === 'paper') {
        return 'You win'
      } else {
        return 'You lose'
      }
    },
    pc_player() {
      const pc_select = ['rock', 'paper', 'scissors']
      const pc_select_random = pc_select[Math.floor(Math.random() * pc_select.length)]
      this.pc_select = pc_select_random
      return pc_select_random
    },
  }
}
</script>

<style scoped>
@import url('@/assets/css/Playground/style.css');
</style>
