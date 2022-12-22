<template>
    <div class="playground">
      <div class="player_select">
        <div class="player_select_options">
          <div class="player_select_option" id="rock" @click="player_select='rock'">
            <img src="@/assets/img/icon-rock.svg" alt="rock">
          </div>
          <div class="player_select_option" id="paper" @click="player_select='paper'">
            <img src="@/assets/img/icon-paper.svg" alt="paper">
          </div>
          <div class="player_select_option" id="scissors" @click="player_select='scissors'">
            <img src="@/assets/img/icon-scissors.svg" alt="scissors">
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
      player_select: null
    }
  },
}
</script>

<style scoped>
@import url('@/assets/css/Playground/style.css');
</style>
