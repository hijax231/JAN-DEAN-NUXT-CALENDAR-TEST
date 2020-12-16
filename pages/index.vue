<template>
  <div class="wrapper">
    <div class="calendar">
      <calendarhead v-bind:datedata="datedata" />
      <calendarbody v-bind:datedata="datedata" />
    </div>
    <addtask />
  </div>
</template>

<script>
import moment from "moment";
import addtask from "../components/calendar/addtask.vue";
import calendarhead from "../components/calendar/calendarheader.vue";
import calendarbody from "../components/calendar/calendarbody.vue";
export default {
  data() {
    return {
      datedata: {
        today: moment(),
        datehandler: moment(),
        year: "",
        month: "",
        day: "",

        tasklist: [
          {
            id: "0",
            title: "Deans Birthday",
            seletectedday: "10",
            seletectedyear: "2020",
            seletectedmonth: "December",
          },
        ],
      },
    };
  },
  components: {
    calendarhead,
    addtask,
    calendarbody,
  },
};
</script>

<style>
body {
  background: grey;

  /* display: grid;
  grid-template-columns: repeat(2 , 1fr); */
}
.wrapper {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
}

.calendar {
  margin: 0 auto;
  width: 90%;
  background: #e8e8e8;
  box-shadow: 5px 10px black;
  padding: 20px;
  display: grid;
  grid-row-gap: 10px;
}
</style>