<template>
  <div v-show="check">
    <li v-for="p in participants" :key="p.name">{{ p.name }}</li>
  </div>
</template>

<script>
export default {
  data() {
    return {
      oldCounter: 0
    };
  },
  props: ["participants", "counter"],
  computed: {
    check() {
      if (this.oldCounter != this.counter) {
        this.oldCounter = this.counter;
        return true;
      } else {
        return false;
      }
    }
  }
};
</script>

<style>
</style>