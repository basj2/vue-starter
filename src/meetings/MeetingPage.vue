<template>
  <!--<div v-if="meetings.length > 0">
    <h2>Zajęcia</h2>
    <new-meeting-form @added="addNewMeeting($event)"></new-meeting-form>
    <meetings-list :meetings="meetings"></meetings-list>
  </div>-->
  <div>
    <div v-if="newMeetingForm == false">
      <button @click="openMeetingForm()">Dodaj nowe spotkanie</button>
    </div>

    <div v-else>
      <h2>Dodaj nowe spotkanie</h2>
      <new-meeting-form @added="addNewMeeting($event)"></new-meeting-form>
    </div>

    <div v-if="meetings.length == 0">
      <h5>Brak zaplanowanych spotkań.</h5>
    </div>
    <div v-else>
      <h5>Zaplanowane spotkania ({{meetings.length}})</h5>
      <meetings-list :meetings="meetings"></meetings-list>
    </div>
  </div>
</template>

<script>
import NewMeetingForm from "./NewMeetingForm";
import MeetingsList from "./MeetingsList";

export default {
  components: { NewMeetingForm, MeetingsList },
  data() {
    return {
      meetings: [],
      newMeetingForm: false
    };
  },
  methods: {
    addNewMeeting(meeting) {
      this.meetings.push(meeting);
      this.newMeetingForm = false;
    },
    openMeetingForm() {
      this.newMeetingForm = true;
    }
  }
};
</script>

<style>
</style>