<template>
  <v-container>
    <v-row justify="center">
      <v-col style="display: none">
        <v-chip-group
          class="mx-auto"
          v-model="selectedComponent"
          mandatory
          active-class="primary--text"
        >
          <v-chip @click="hello" outlined large v-for="tag in tags" :key="tag">
            {{ tag }}
          </v-chip>
        </v-chip-group>
      </v-col>
    </v-row>
    <v-row style="">
      <v-col cols="12" class="text-center" v-if="selectedComponent === 0">
        <div class="date">
          <!-- التحويل من هجري إلي ميلادي -->
          <v-row>
            <v-col>
              <h5>التحويل من هجري إلي ميلادي</h5>
            </v-col>
          </v-row>
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
                :items="getMonthsMenu('hijri')"
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
            <v-col>
              <Copy :text="currentDate.format('YYYY/MM/DD')+' م'" />
              <Copy :text="currentDate.format('DD MMMM YYYY ')+' م'" />
            </v-col>
          </v-row>
        </div>

        <v-spacer></v-spacer>
        <!-- التحويل من ميلادي إلي هجري -->
        <div class="date">
          <v-row style="margin-top: 50px">
            <v-col>
              <h5>التحويل من ميلادي إلي هجري</h5>
            </v-col>
          </v-row>
          <v-row justify="center">
            <v-col cols="4" md="2">
              <v-autocomplete
                v-model="selectedDay2"
                :items="getDaysMenu()"
                label="إختر اليوم"
              ></v-autocomplete>
            </v-col>
            <v-col cols="4" md="2">
              <v-autocomplete
                v-model="selectedMonth2"
                label="إختر الشهر"
                :item-text="(item) => item.value + ' - ' + item.text"
                :items="getMonthsMenu()"
              ></v-autocomplete>
            </v-col>
            <v-col cols="4" md="2">
              <v-autocomplete
                v-model="selectedYear2"
                label="إختر العام"
                :items="getYeasMenu()"
              ></v-autocomplete>
            </v-col>
          </v-row>
          <v-row v-if="currentDate2">
            <v-col>
              <Copy :text="currentDate.format('iYYYY/iMM/iDD')+' هـ'" />
              <Copy :text="currentDate.format('iDD iMMMM iYYYY')+' هـ'" />
            </v-col>
          </v-row>
        </div>
      </v-col>
      <v-col
        cols="12"
        class="date text-center"
        v-else-if="selectedComponent === 2"
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
          <v-col>
            <Copy :text="currentDate.format('iYYYY/iMM/iDD')" />
            <Copy :text="currentDate.format('iDD iMMMM iYYYY')" />
          </v-col>
        </v-row>
      </v-col>
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
          <v-col>
            <Copy :text="currentDate.format('YYYY/MM/DD')" />
            <Copy :text="currentDate.format('DD MMMM YYYY ')" />
          </v-col> </v-row
      ></v-col>
    </v-row>
  </v-container>
</template>

<script>
let moment = require('moment-hijri')
import { ArabicMonths, ArabicGregMonths } from './script'
import Copy from './copyText'

export default {
  components: {
    Copy,
  },
  name: 'HelloWorld',
  mounted() {
    this.hijriDate = moment().format('iYYYY/iM/iD')
    this.gregDate = moment().format('ll')
  },
  head() {
    return {
      title: `
تحويل التاريخ | تحويل التاريخ من هجري الى ميلادي | تحويل التاريخ من ميلادي الى هجري | تاريخ اليوم في السعودية
 `,
      meta: [
        // hid is used as unique identifier. Do not use `vmid` for it as it will not work
        {
          hid: 'description',
          name: 'description',
          content: `منصة هجري السعودية تقوم بـ تحويل التاريخ من هجري لميلادي  و تحويل التاريخ من ميلادي الى هجري و تحويل من هجري لميلادي و التاريخ ميلادي و كذلك التاريخ الميلادي والهجري اليوم`,
        },
      ],
    }
  },
  watch: {
    selectedComponent(value) {
      if (value === 2) this.dateType = 'greg'
      else this.dateType = 'hijri'
    },
  },
  methods: {
    hello() {
      // ! enable this if you remove the script from nuxt head
      // gtag("event", 'conversion', {'send_to': 'AW-955968979/468HCODz6pQDENPb68cD'}); 
    },
    getMonthsMenu(type) {
      return type === 'hijri' ? ArabicMonths() : ArabicGregMonths()
    },
    getDaysMenu(dateType) {
      let arr = []
      if (dateType === 'hijri') {
        for (let i = 1; i <= 30; i++) {
          arr.push(i)
        }
      } else {
        for (let i = 1; i <= 31; i++) {
          arr.push(i)
        }
      }
      return arr
    },
    getYeasMenu(dateType) {
      let arr = []
      if (dateType === 'hijri') {
        for (let i = 1500; i >= 0; i--) {
          arr.push(i)
        }
      } else {
        for (let i = 2100; i >= 1700; i--) {
          arr.push(i)
        }
      }
      return arr
    },
  },
  computed: {
    currentDate2() {
      if (this.selectedYear2 && this.selectedMonth2 && this.selectedYear2) {
        return moment(
          this.selectedDay2 +
            ' ' +
            this.selectedMonth2 +
            ' ' +
            this.selectedYear2,
          'DD MM YYYY'
        )
      } else return null
    },
    currentDate() {
      if (this.selectedYear && this.selectedMonth && this.selectedYear) {
        if (this.dateType === 'hijri')
          return moment(
            this.selectedDay +
              ' ' +
              this.selectedMonth +
              ' ' +
              this.selectedYear,
            'iDD iMM iYYYY'
          )
        else {
          return moment(
            this.selectedDay +
              ' ' +
              this.selectedMonth +
              ' ' +
              this.selectedYear,
            'DD MM YYYY'
          )
        }
      } else return null
    },
    date() {
      return (
        this.selectedYear + '-' + this.selectedMonth + '-' + this.selectedDay
      )
    },
    days() {
      let arr = []
      if (this.dateType === 'hijri') {
        for (let i = 1; i <= 30; i++) {
          arr.push(i)
        }
      } else {
        for (let i = 1; i <= 31; i++) {
          arr.push(i)
        }
      }
      return arr
    },
    months() {
      return this.dateType === 'hijri' ? ArabicMonths() : ArabicGregMonths()
    },

    years() {
      let arr = []
      if (this.dateType === 'hijri') {
        for (let i = 1500; i >= 0; i--) {
          arr.push(i)
        }
      } else {
        for (let i = 2100; i >= 1700; i--) {
          arr.push(i)
        }
      }
      return arr
    },
  },
  data: () => ({
    ggg: 'ggg',
    selectedYear: '',
    selectedMonth: '',
    selectedDay: '',
    selectedYear2: '',
    selectedMonth2: '',
    selectedDay2: '',
    selectedComponent: 0,
    hijriDate: '',
    gregDate: '',
    dateType: 'hijri',
    tags: [
      'تحويل التاريخ',
      'تحويل التاريخ من هجري إلي ميلادي   ',
      'تحويل التاريخ من ميلادي إلي هجري ',
    ],
  }),
}
</script>

<style>
.date {
  background-color: #e4fae4;
  border-radius: 10px;
  font-size: 2rem;
}
.container{
padding: 3%;
}
@media screen and (max-width: 640px){
.container{
padding: 2%;
margin-top: 20px;
}
}
</style>
