<template>
  <button class="carousel-control left" @click="$emit('prev')">&lt;&lt;</button>
  <button class="carousel-control right" @click="$emit('next')">
    &gt;&gt;
  </button>
</template>

<script>
export default {
  emits: ["prev", "next"],
};
</script>

<style scoped>
.carousel-control {
  background-color: var(--light);
  border: none;
  border-radius: 50%;
  opacity: 60%;
  display: inline-block;
  position: absolute;
  height: 45px;
  width: 50px;
  top: calc(50% - 25px);
  color: var(--accent);
  cursor: pointer;
}

.left {
  left: 0;
}

.right {
  right: 0;
}
</style>
