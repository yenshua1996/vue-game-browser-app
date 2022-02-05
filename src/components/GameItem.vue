<template>
  <article class="card">
    <div class="card-background">
      <img class="game-image" :src="game.background_image" alt="" />
    </div>

    <div class="card-content">
      <div class="card-header">
        <h5 class="card-title">{{ game.name }}</h5>

        <div class="game-genres">
          <div class="genre" v-for="{ name, id } in game.genres" :key="id">
            <p class="genre-content">{{ name }}</p>
          </div>
        </div>
      </div>

      <div class="card-control">
        <Button
          @btn-click="$emit('btn-click', game.id)"
          content="fas fa-binoculars"
          :gameId="game.id"
        />

        <Button content="fas fa-shopping-cart" />

        <Button content="fas fa-magic" />
      </div>
    </div>
  </article>
</template>

<script>
import Button from "./Button.vue";

export default {
  name: "GameItem",
  props: {
    game: Object,
  },

  components: {
    Button,
  },

  create() {
    console.log(this.game);
  },
};
</script>

<style scoped>
.card {
  border-radius: 5px;
  overflow: hidden;
  position: relative;
  height: 100%;
  box-shadow: 0 3px 6px rgba(0, 0, 0, 0.19), 0 3px 6px rgba(0, 0, 0, 0.23);
  transition: transform 300ms ease-in-out;
}

.card::before {
  content: "";
  position: absolute;
  height: 100%;
  width: 100%;
  z-index: -1;
  background: linear-gradient(
    to right,
    rgb(10, 10, 10),
    rgba(255, 255, 255, 0)
  );
}

.card-background {
  position: absolute;
  top: 0;
  left: 0;
  z-index: -2;
  height: 100%;
}

.card-content {
  padding: 1rem;
}

.card-header {
  margin-bottom: 58%;
}

.card-title {
  font-size: 1.25rem;
  font-weight: 500;
  color: #fff;
}

.genre-content {
  font-weight: 400;
  font-size: 0.825rem;
  color: rgb(228, 228, 228);
}

.game-image {
  display: block;
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.game-genres {
  display: flex;
  gap: 0.5rem;
  align-items: center;
}

.card-control {
  display: none;
}

.card:hover {
  cursor: pointer;
  transform: scale(1.1);
}

.card:hover .card-control {
  display: block;
}
</style>
