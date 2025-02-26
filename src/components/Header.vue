<template>
  <div class="header">
    <span v-for="link in links" :key="link" @click="$emit('linkClick', link)">{{
      link
    }}</span>
  </div>
</template>

<script>
export default {
  emits: ["linkClick"],
  data() {
    return {
      links: ["Home", "About", "Feedback"],
    };
  },
};
</script>

<style scoped>
span {
  border: 1px dashed var(--warm);
  padding: 10px;
  border-radius: 20px;
  cursor: pointer;
}
</style>
