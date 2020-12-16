<template>
  <div class="calendarbody">
    <ul class="calendardates">
      <li class="weeks" v-for="week in weeks">
        {{ week }}
      </li>
      <li class="blanks" v-for="blank in getfirstday">
        {{ getfirstblanks + blank }}
      </li>
      <li
        v-for="days in getdaysinmonth"
        :class="{
          currentday:
            days == datetoday &&
            monthtoday == datedata.month &&
            yeartoday == datedata.year,
        }"
      >
        {{ days }}
      </li>

      <li class="blanks" v-for="last in getlastblanks">
        {{ last }}
      </li>
    </ul>
  </div>
</template>

<script>
import moment from "moment";

export default {
  props: ["datedata"],
  data() {
    return {
      weeks: [
        "Sunday",
        "Monday",
        "Tuesday",
        "Wenesday",
        "Thursday",
        "Friday",
        "Saturday",
      ],
    };
  },
  computed: {
    getdaysinmonth() {
      return this.datedata.datehandler.daysInMonth();
    },
    getfirstday() {
      var firstday = moment(this.datedata.datehandler).subtract(
        this.getcurentdate - 1,
        "days"
      );
      return firstday.weekday();
    },
    getcurentdate() {
      return this.datedata.datehandler.get("date");
    },
    getfirstblanks() {
      var lastmonth = moment(this.datedata.datehandler).subtract("1", "month");
      return this.getdaysinmonth - this.getfirstday;
    },
    getlastblanks() {
      return 42 - (this.getfirstday + this.getdaysinmonth);
    },
    datetoday() {
      return this.datedata.today.get("date");
    },
    monthtoday() {
      return this.datedata.today.format("MMMM");
    },
    yeartoday() {
      return this.datedata.today.format("Y");
    },
  },
};
</script>

<style>
.calendardates {
  display: grid;
  grid-template-columns: repeat(7, 1fr);
  grid-template-rows: repeat(7, 1fr);
  text-align: center;
  list-style: none;
  padding: 0px;
}
.calendardates li {
  position: relative;
  border: 1px solid black;
  padding: 10px;
}
.blanks {
  background: grey;
  color: white;
}
.weeks {
  background: blue;
  color: white;
}
.currentday {
  background: green;
  color: white;
}
</style>