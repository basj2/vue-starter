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
        <button
          v-if="meeting.participants.length == 0"
          @click="removeEmptyMeeting(meeting)"
          style="float: right;margin:5px;"
        >Usuń puste spotkanie</button>
        <button
          v-if="!checkUser(meeting)"
          @click="addUser(meeting)"
          style="color:#9b4dca;background:white;float:right;margin:5px;"
        >Zapisz się</button>
        <button
          v-else
          @click="removeUser(meeting)"
          style="color:#9b4dca;background:white;float:right;margin:5px;"
        >Wypisz się</button>
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
      id: 0
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
      var i;
      var j;
      for (j = 0; j < meeting.participants.length; j++) {
        if (meeting.participants[j].name == this.username) {
          i = j;
        }
      }

      meeting.participants.splice(i, 1);
      this.counter -= 1;
      this.test = i;
    },

    removeEmptyMeeting(meeting) {
      var i = this.meetings.indexOf(meeting);
      this.meetings.splice(i, 1);
    }
  },
  computed: {}
};
</script>

<style>
</style>