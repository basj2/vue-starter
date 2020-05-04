<template>
  <div id="app">
    <h1>Witaj w systemie do zapisów na zajęcia</h1>
    <div v-if="!authenticatedUsername">
      <login-form @login="logMeIn($event)"></login-form>
    </div>
    <div v-else>
      <logged-in-user :username="authenticatedUsername" @logout="logMeOut()"></logged-in-user>
    </div>
  </div>
</template>

<script>
import "milligram";
import LoginForm from "./LoginForm";
import LoggedInUser from "./LoggedInUser";
export default {
  components: { LoginForm, LoggedInUser },
  
  data() {
    return {
      authenticatedUsername: ""
    };
  },
  methods: {
    logMeIn(username) {
      this.authenticatedUsername = username;
    },
    logMeOut() {
      this.authenticatedUsername = "";
    }
  }
};
</script>


<style>
</style>
