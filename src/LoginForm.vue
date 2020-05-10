<template>
  <form @submit.prevent="enter()">
    <label>Zaloguj się e-mailem</label>
    <input type="email" v-model="email" />
    <button>{{ buttonLabelToDisplay }}</button>
  </form>
</template>

<script>
export default {
  props: ["buttonLabel"],
  data() {
    return {
      email: ""
    };
  },
  methods: {
    enter() {
      this.$emit("login", this.email);
      this.email = "";
    }
  },
  computed: {
    buttonLabelToDisplay() {
      return this.buttonLabel || "Zaloguj się";
    }
  }
};
</script>

<style>
</style>