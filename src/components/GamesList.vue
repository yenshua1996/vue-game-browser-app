<template>
  <div class="games-list">
    <div class="game-item" v-for="game in games" :key="game.id">
      <GameItem @btn-click="$emit('btn-click', game.id)" :game="game" />
    </div>
  </div>
</template>

<script>
import GameItem from "./GameItem.vue";

export default {
  name: "GamesList",

  props: {
    games: Array,
  },

  components: {
    GameItem,
  },
};
</script>

<style scoped>
.games-list {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(20%, 1fr));
  grid-auto-rows: 300px;
  gap: 2rem;
}
</style>
