<template>
  <div id="app">
    <h1>Witaj w systemie do zapisów na zajęcia</h1>
    <div v-show="!authenticatedUsername">
      <login-form @login="logMeIn($event)"></login-form>
    </div>
    <div v-show="authenticatedUsername">
      <logged-in-user :username="authenticatedUsername" @logout="logMeOut()"></logged-in-user>

      <meeting-page :username="authenticatedUsername"></meeting-page>
    </div>
  </div>
</template>

<script>
import "milligram";
import LoginForm from "./LoginForm";
import LoggedInUser from "./LoggedInUser";
import MeetingPage from "./meetings/MeetingPage";

export default {
  components: { LoginForm, LoggedInUser, MeetingPage },

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
