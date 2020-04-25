<template>
  <div id="app">
    <h1>Witaj w systemie do zapisów na zajêcia</h1>

    <!---<div v-if="email.length < 10">Ale masz krótki adres!</div>
    <div v-else-if="email.length < 15">Twój adres e-mail jest w sam raz.</div>
    <div v-else>Twój adres e-mail jest stanowczo za d³ugi.</div>-->
    <div v-if="!authenticatedUserName">
      <login-form @login="logMeIn($event)" button-label="WejdŸ"></login-form>
      <login-form @login="logMeIn($event)" button-label="Wleæ"></login-form>
      <login-form @login="logMeIn($event)" :button-label="Math.random() < 0.5 ? 'Etykieta A' : 'Etykieta B'"></login-form>
    </div>
    <div v-else>
      <h3>Witaj {{authenticatedUserName}}!</h3>
      <a @click="logMeOut()">Wyloguj</a>
    </div>
  </div>
</template>

<script>
import "milligram";
import LoginForm from "./LoginForm";
export default {
  components: {LoginForm},
  data() {
    return {
      authenticatedUserName: ""
    };
  },
  methods: {
    alertMyEmail() {
      alert(this.email);
    },
    logMeIn(username) {
      this.authenticatedUserName = username;
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
