<template>
  <v-container style="padding:5%">
    <v-row justify="center">
      <v-col style="display:grid;">
        <v-chip-group
          class="mx-auto"
          v-model="selectedComponent"
          mandatory
          active-class="primary--text"
        >
          <v-chip outlined large v-for="tag in tags" :key="tag">
            {{ tag }}
          </v-chip>
        </v-chip-group>
      </v-col>
    </v-row>
    <v-row>
      <v-col cols="12" class="date text-center" v-if="selectedComponent === 0"
        >1</v-col
      >
      <v-col
        cols="12"
        class="date text-center"
        v-else-if="selectedComponent === 1"
      >
        <v-row justify="center">
          <v-col cols="4" md="2">
            <v-autocomplete
              v-model="selectedDay"
              :items="days"
              label="إختر اليوم"
            ></v-autocomplete>
          </v-col>
          <v-col cols="4" md="2">
            <v-autocomplete
              v-model="selectedMonth"
              label="إختر الشهر"
              :item-text="(item) => item.value + ' - ' + item.text"
              :items="months"
            ></v-autocomplete>
          </v-col>
          <v-col cols="4" md="2">
            <v-autocomplete
              v-model="selectedYear"
              label="إختر العام"
              :items="years"
            ></v-autocomplete>
          </v-col>
        </v-row>
        <v-row v-if="currentDate">
          <v-col> {{ currentDate.format("iDD iMMMM iYYYY") }}</v-col>
        </v-row>
      </v-col>
      <v-col cols="12" class="date text-center" v-else>
        <v-row justify="center">
          <v-col cols="4" md="2">
            <v-autocomplete
              v-model="selectedDay"
              :items="days"
              label="إختر اليوم"
            ></v-autocomplete>
          </v-col>
          <v-col cols="4" md="2">
            <v-autocomplete
              v-model="selectedMonth"
              label="إختر الشهر"
              :item-text="(item) => item.value + ' - ' + item.text"
              :items="months"
            ></v-autocomplete>
          </v-col>
          <v-col cols="4" md="2">
            <v-autocomplete
              v-model="selectedYear"
              label="إختر العام"
              :items="years"
            ></v-autocomplete>
          </v-col>
        </v-row>
        <v-row v-if="currentDate">
          <v-col> {{ currentDate.format("ll") }}</v-col>
        </v-row></v-col
      >
    </v-row>
  </v-container>
</template>

<script>
let moment = require("moment-hijri");
import { ArabicMonths, ArabicGregMonths } from "./script";

export default {
  name: "HelloWorld",
  mounted() {
    this.hijriDate = moment().format("iYYYY/iM/iD");
    this.gregDate = moment().format("ll");
  },
  watch: {
    selectedComponent(value) {
      if (value === 1) this.dateType = "greg";
      else this.dateType = "hijri";
    },
  },
  computed: {
    currentDate() {
      if (this.selectedYear && this.selectedMonth && this.selectedYear) {
        if (this.dateType === "hijri")
          return moment(
            this.selectedDay +
              " " +
              this.selectedMonth +
              " " +
              this.selectedYear,
            "iDD iMM iYYYY"
          );
        else {
          return moment(
            this.selectedDay +
              " " +
              this.selectedMonth +
              " " +
              this.selectedYear,
            "DD MM YYYY"
          );
        }
      } else return null;
    },
    date() {
      return (
        this.selectedYear + "-" + this.selectedMonth + "-" + this.selectedDay
      );
    },
    days() {
      let arr = [];
      if (this.dateType === "hijri") {
        for (let i = 1; i <= 30; i++) {
          arr.push(i);
        }
      } else {
        for (let i = 1; i <= 31; i++) {
          arr.push(i);
        }
      }
      return arr;
    },
    months() {
      return this.dateType === "hijri" ? ArabicMonths() : ArabicGregMonths();
    },

    years() {
      let arr = [];
      if (this.dateType === "hijri") {
        for (let i = 1442; i >= 0; i--) {
          arr.push(i);
        }
      } else {
        for (let i = 2021; i >= 1500; i--) {
          arr.push(i);
        }
      }
      return arr;
    },
  },
  data: () => ({
    ggg: "ggg",
    selectedYear: "",
    selectedMonth: "",
    selectedDay: "",
    selectedComponent: 2,
    hijriDate: "",
    gregDate: "",
    dateType: "hijri",
    tags: [
      "تاريخ اليوم",
      "تحويل التاريخ من ميلادي إلي هجري ",
      "تحويل التاريخ من هجري إلي ميلادي   ",
    ],
  }),
};
</script>

<style>
.date {
  background-color: #eff3fd;
  border-radius: 10px;
  font-size: 2rem;
}
</style>
