<template>
  <div class="container">
    <Header @search-title="searchTitle" />
    <GamesList @btn-click="viewGame" :games="games" />
    <Footer />
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import GamesList from "./components/GamesList.vue";
import Footer from "./components/Footer.vue";

export default {
  name: "App",

  components: {
    Header,
    GamesList,
    Footer,
  },
  emits: ["search-title", "btn-click"],

  data() {
    return {
      apiKey: "ad05e306a8834be49c380bd53853a7de",
      games: [],
      cart: [],
    };
  },

  methods: {
    searchTitle(query) {
      console.log(query);

      console.log(this.cart);
    },

    addCart(game) {
      console.log(this.cart);
    },

    async viewGame(id) {
      const res = await fetch(
        `https://api.rawg.io/api/games/${id}?key=${this.apiKey}`
      );

      const game = await res.json();

      console.log(game);
    },

    async fetchGames() {
      const res = await fetch(
        `https://api.rawg.io/api/games?key=${this.apiKey}`
      );

      const { results } = await res.json();

      console.log(results);

      return results;
    },
  },

  async created() {
    this.games = await this.fetchGames();
  },
};
</script>

<style>
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}

body {
  font-family: "roboto", sans-serif;
  line-height: 1.6;
}

button {
  border: none;
  border-radius: 0;
  display: inline-block;
}

button:focus {
  outline: none;
}

button:hover {
  cursor: pointer;
}

input {
  display: inline-block;
  width: 100%;
  border-radius: 5px;
  padding: 0.5rem;
  border: 2px solid rgb(202, 202, 202);
}

input::placeholder {
  font-family: "roboto", sans-serif;
}

input:focus {
  outline: none;
}

h1,
h2,
h3,
h4,
h5 {
  font-weight: 400;
  line-height: 1.2;
}

.container {
  width: 95%;
  margin: 0 auto;
}

.btn {
  padding: 0.5rem 1.5rem;
  border-top-right-radius: 5px;
  border-bottom-right-radius: 5px;
}
</style>
