<template>
  <button @click="$emit('btn-click')" class="btn">
    <i :class="content"></i>
  </button>
</template>

<script>
export default {
  name: "Button",
  props: {
    content: String,
    gameId: Number,
  },
};
</script>

<style scoped>
.btn {
  display: inline-block;
  padding: 1rem;
  border-radius: 4px;
  margin-right: 1rem;
  background: #fff;
  transition: transform 200ms linear;
}

.btn:hover {
  transform: translateY(-4px);
}
</style>
