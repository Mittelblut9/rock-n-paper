<template>
  <Scoreboard/>
  <Playground/>
</template>

<script>
import Scoreboard from '@/components/Scoreboard.component.vue'
import Playground from '@/components/Playground.component.vue'

export default {
  name: 'HomeView',
  components: {
    Scoreboard,
    Playground
  }
}
</script>
