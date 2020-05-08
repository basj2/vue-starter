<template>
  <form @submit.prevent="addNewMeeting()">
    <h3>Dodaj nowe spotkanie</h3>
    <label>Nazwa</label>
    <input type="text" v-model="newMeeting.name" />
    <label>Opis</label>
    <textarea v-model="newMeeting.description"></textarea>
    <button>Dodaj</button>
    <span style="color:red">{{error}}</span>
  </form>
</template>

<script>
export default {
  data() {
    return {
      newMeeting: {},
      error: ""
    };
  },
  methods: {
    addNewMeeting() {
      this.newMeeting.participants = [];
      if (!this.newMeeting.name) {
        this.error = "Spotkanie musi mieć nazwę";
      } else {
        this.$emit("added", this.newMeeting);
      }
      this.newMeeting = {};
    }
  }
};
</script>

<style>
</style>