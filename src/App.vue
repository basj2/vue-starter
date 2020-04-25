<template>
  <div id="app">
    <h1>Witaj w systemie do zapisów na zajêcia</h1>

    <!---<div v-if="email.length < 10">Ale masz krótki adres!</div>
    <div v-else-if="email.length < 15">Twój adres e-mail jest w sam raz.</div>
    <div v-else>Twój adres e-mail jest stanowczo za d³ugi.</div>-->
    <div v-if="!authenticatedUserName">
      Zaloguj siê e-mailem
      <input type="email" v-model="email" />
      <button @click="logMeIn()">Wchodzê</button>
    </div>
    <div v-else>
      <h3>Witaj {{authenticatedUserName}}!</h3>
      <a @click="logMeOut()">Wyloguj</a>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      email: "",
      authenticatedUserName: ""
    };
  },
  methods: {
    alertMyEmail() {
      alert(this.email);
    },
    logMeIn() {
      this.authenticatedUserName = this.email;
      this.email = "";
    },
    logMeOut() {
      this.authenticatedUserName = "";
    }
  }
};
</script>

<style>
</style>
