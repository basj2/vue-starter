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
          <meeting-participants  :counter ="counter" :participants="meeting.participants"></meeting-participants>
        </td>

        <button style="float: right;margin:5px;">Usuń puste spotkanie</button>
        <button @click="addUser(meeting)" style="float: right;margin:5px;">Zapisz się</button>
      </tr>
    </tbody>
  </table>
</template>

<script>
import MeetingParticipants from "./MeetingParticipants";

export default {
  components: { MeetingParticipants },
  data() {
      return{
          counter: 0,
      }
     
  },
  props: ["meetings"],
  methods: {
    addUser(meeting) {
      this.$emit("userAdded", meeting);
      this.counter += 1
          }
  },


};
</script>

<style>
</style>