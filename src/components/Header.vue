<template>
  <header class="header">
    <div class="column flex-item-2">
      <form @submit.prevent="onSubmit()" class="form-panel">
        <input
          type="text"
          class="form-input"
          placeholder="Search..."
          v-model="searchInput"
        />
        <button class="btn btn-search">🔎</button>
      </form>
    </div>

    <div class="column">
      <div class="cart-element">🛒</div>
    </div>
  </header>
</template>

<script>
export default {
  name: "Header",
  data() {
    return {
      searchInput: "",
    };
  },

  methods: {
    onSubmit() {
      this.$emit("search-title", this.searchInput);

      this.searchInput = "";
    },
  },
};
</script>

<style scoped>
.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 2rem 0;
  margin-bottom: 2rem;
  gap: 70%;
}

.flex-item-2 {
  flex-grow: 1;
}

.form-panel {
  display: flex;
  justify-content: space-between;
}

.form-input {
  border-top-right-radius: 0;
  border-bottom-right-radius: 0;
}

.btn-search {
  background-color: rgb(41, 41, 41);
}

.btn-search:hover {
  background-color: rgb(223, 223, 223);
}
</style>
