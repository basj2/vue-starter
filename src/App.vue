<template>
  <div id="app">
    <h1>Twój adres e-mail to {{ email }}</h1>

    <div v-if="email.length < 10">Ale masz krótki adres!</div>
    <div v-else-if="email.length < 15">Twój adres e-mail jest w sam raz.</div>
    <div v-else>Twój adres e-mail jest stanowczo za d³ugi.</div>
    <input type="email" v-model="email" />
    <button @click="alertMyEmail()">Wyœwietl mój adres e-mail w alercie</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      email: ""
    };
  },
  methods: {
    alertMyEmail() {
      alert(this.email);
    }
  }
};
</script>

<style>
</style>
