<template>
  <div class="Scheduler">
    <Live />
    <div class="schedule-block" style="margin-top:5%;">
      <div class="select-date">
        <div v-on:click="changeSat" class="date-tag" v-bind:class="[sat_day ? 'active-tag' : 'inactive-tag']">
          <span> Saturday </span>
        </div>
        <div v-on:click="changeSun" class="date-tag" v-bind:class="[sat_day ? 'inactive-tag' : 'active-tag']">
          <span> Sunday </span>
        </div>
      </div>
      <Schedule v-if="sat_day" :events="sat_events" :timelines="sat_timeline" />
      <Schedule v-else :events="sun_events" :timelines="sun_timeline" />
    </div>
    <b-container fluid>
      <Flair />
    </b-container>
  </div>
</template>

<script>
  import Schedule from "./Schedule.vue"
  import Live from "../components/Live.vue"
  import Flair from "../components/Flair.vue"

export default {
  name: "SchedulePage",
  components: {
    Schedule,
    Live,
    Flair
  },
  data() {
    return {
      animating: false,
      sat_day: true,
      sat_timeline: [
        "9:00", "9:30", "10:00", "10:30", "11:00", "11:30", "12:00",
        "12:30", "13:00", "13:30", "14:00", "14:30", "15:00", "15:30",
        "16:00", "16:30", "17:00", "17:30", "18:00", "18:30", "19:00", "19:30", "20:00",
        "20:30", "21:00", "21:30", "22:00", "22:30", "23:00", "23:30", "24:00"
      ],
      sun_timeline: [
        "0:00", "0:30", "1:00", "1:30", "2:00", "2:30", "3:00", "3:30", "4:00", "4:30", "5:00", "5:30",
        "6:00", "6:30", "7:00", "7:30", "8:00", "8:30","9:00", "9:30", "10:00", "10:30", "11:00", "11:30", "12:00",
        "12:30", "13:00", "13:30", "14:00", "14:30", "15:00", "15:30"
      ],
      sat_events: [ // three categories
        {
          name: "General",
          event_list:
          [
            {
              location: "Metcalf Ballroom",
              start: "9:00",
              end: "10:30",
              type: "event-2",
              full_name: "Check-in"
            },
            {
              start: "11:00",
              end: "12:00",
              type: "event-2",
              full_name: "Opening Ceremony"
            },
            {
              location: "Terrance Lounge",
              start: "12:00",
              end: "13:00",
              type: "event-2",
              full_name: "Team formation"
            },
            {
              location: "Conference Auditorium",
              start: "13:00",
              end: "14:00",
              type: "event-2",
              full_name: "Stakeholder Talks"
            },
            {
              locattion: "Room 310",
              start: "14:00",
              end: "15:00",
              type: "event-2",
              full_name: "Women in Tech Meetup"
            },
            {
              location: "Hacking Area",
              start: "12:30",
              end: "13:00",
              type: "event-2",
              full_name: "Lunch"
            },
            {
              start: "18:30",
              end: "19:00",
              type: "event-2",
              full_name: "Dinner"
            },
            {
              location: "Conference Auditorium and Terrace Lounge",
              start: "22:00",
              end: "24:00",
              type: "event-2",
              full_name: "Movies"
            },
          ]
        },
        {
          name: "Flash Workshops",
          event_list:
          [
            {
              location: "GSU 310",
              start: "20:00",
              end: "20:30",
              type: "event-1",
              full_name: "Starting Up Your Start-up"
            },
            {
              location: "GSU 310",
              start: "20:30",
              end: "21:00",
              type: "event-1",
              full_name: "No Such Thing as Black Magic"
            },
            {
              location: "GSU 310",
              start: "21:00",
              end: "22:15",
              type: "event-1",
              full_name: "Skyrim Modding from a Skyrim Modder"
            }
          ]
        }
      ],
      sun_events:[
        {
          name: "General",
          event_list:
          [
            {
              location: "BU Academy Room",
              start: "00:00",
              end: "1:00",
              type: "event-2",
              full_name: "Midnight Snack"
            },
            {
              start: "8:00",
              end: "9:00",
              type: "event-2",
              full_name: "Breakfast"
            },
            {
              start: "9:00",
              end: "10:00",
              type: "event-2",
              full_name: "Submissions due (10AM)"
            },
            {
              location: "BU Academy Room",
              start: "11:00",
              end: "12:00",
              type: "event-2",
              full_name: "Lunch"
            },
            {
              start: "12:00",
              end: "13:30",
              type: "event-2",
              full_name: "Judging"
            },
            {
              start: "14:00",
              end: "15:00",
              type: "event-2",
              full_name: "Closing Ceremony"
            },
          ],
        },
        {
          name: "Side Events",
          event_list:
          [
            {
              location: "Second Floor Metcalf",
              start: "00:00",
              end: "1:00",
              type: "event-1",
              full_name: "Pinata"
            },
            {
              location: "Conference Auditorium and Terrace Lounge",
              start: "1:00",
              end: "4:00",
              type: "event-1",
              full_name: "Movies"
            },
            {
              start: "8:00",
              end: "9:00",
              type: "event-1",
              full_name: "Yoga"
            },
          ]
        }
      ]
    }
  },
  methods: {
    changeSat: function() {
      this.sat_day = true
    },
    changeSun: function() {
      this.sat_day = false
    }
  }
};
</script>

<style scoped>
#bolder {
  font-weight: 700;
  text-align: center;
}

#redot {
  border: 1px solid #f05352;
  border-radius: 50px;
  background-color: #f05352;
  height: 0.75vw;
  width: 0.75vw;
  display: inline-block;
}

.schedule-block {
  width: 80%;
  margin-left: auto;
  margin-right: auto;
  margin-bottom: auto;
  margin-top: 4vh;
  background-color: white;
}

.select-date {
  position: relative;
  background-color: #928aa6;
  height: 8vw;
  padding-left: 2vw;
}

.date-tag {
  position: relative;
  top: calc(100% - 4.5vw);
  margin-left: 0.8vw;
  width: 14vw;
  height: 4.5vw;
  display: inline-block;
  font-size: 1.4vw;
}

.date-tag:hover {
  cursor: pointer;
}

.date-tag span {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  font-weight: 900;
}

.active-tag {
  color: #292760;
  background-color: white;
}

.inactive-tag {
  color: white;
  background-color: #a7a1b8;
}
</style>
