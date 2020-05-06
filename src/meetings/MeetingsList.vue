<template>
  <table v-show="meetings.length > 0 ">
    <thead>
      <tr>
        <th>Nazwa spotkania</th>
        <th>Opis</th>
        <th>Uczestnicy</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="meeting in meetings" :key="meeting.name">
        <td>{{ meeting.name }}</td>
        <td>{{ meeting.description }}</td>
        <td>
          <meeting-participants :counter="counter" :participants="meeting.participants"></meeting-participants>
        </td>
        <button v-if="meeting.participants.length == 0" style="float: right;margin:5px;">Usuń puste spotkanie</button>
        <button
          v-if="!checkUser(meeting)" @click="addUser(meeting)" style="float: right;margin:5px;"
        >Zapisz się</button>
        <button v-else @click="removeUser(meeting)" style="float: right;margin:5px;">Wypisz się</button>
        <td>{{test}}</td>
      </tr>
    </tbody>
  </table>
</template>

<script>
import MeetingParticipants from "./MeetingParticipants";
export default {
  components: { MeetingParticipants },
  data() {
    return {
      counter: 0,
      //isAdded: false
      test: "fgnfg",
      added: false
    };
  },
  props: ["meetings", "username"],
  methods: {
    checkUser(meeting) {
      var isAdded = false;
      var i;
      for (i = 0; i < meeting.participants.length; i++) {
        if (meeting.participants[i].name == this.username) {
          isAdded = true;
        }
      }
      return isAdded;
    },
    addUser(meeting) {
      meeting.participants.push({ name: this.username });
      this.counter += 1;
    },
    removeUser(meeting) {
      var i = meeting.participants.indexOf(this.username);
      meeting.participants.splice(i);
      this.counter -= 1;
    }
  },
  computed: {}
};
</script>

<style>
</style>