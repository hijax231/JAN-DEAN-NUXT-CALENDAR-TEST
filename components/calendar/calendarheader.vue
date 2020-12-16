<template>
  <div class="calendarhead">
    <button @click="prevdate" class="btndate"><</button>
    <h4>{{ datedetails }}</h4>
    <button @click="nextdate" class="btndate">></button>
  </div>
</template>

<script>
import moment from "moment";

export default {
  props: ["datedata"],
  computed: {
    year() {
      this.datedata.year = moment(this.datedata.datehandler).format("Y");
      return this.datedata.year;
    },
    month() {
      this.datedata.month = moment(this.datedata.datehandler).format("MMMM");
      return this.datedata.month;
    },
    day() {
      this.datedata.day = moment(this.datedata.datehandler).format("Do");
      return this.datedata.day;
    },
    datedetails() {
      return this.month + " " + this.day + " " + this.year;
    },
  },
  methods: {
    prevdate() {
      this.datedata.datehandler = moment(this.datedata.datehandler).subtract(
        "1",
        "month"
      );
    },
    nextdate() {
      this.datedata.datehandler = moment(this.datedata.datehandler).add(
        "1",
        "month"
      );
    },
  },
};
</script>

<style>
.calendarhead {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-column-gap: 10px;
  justify-items: center;
}

.btndate {
  background: grey;
  color: white;
}
</style>