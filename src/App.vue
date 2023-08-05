<template>
  <Header :header="this.header" />
  <div class="content-container">
    <section class="section-container" id="missions" style="width:335px; height:714px;">
      <div class="section-header clipped-medium-backward">
        <img src="/icons/mission-icon.svg" />
        <h1>Hot off the Press</h1>
      </div>
      <div class="section-content-container">
        <h3>Current Assignment</h3>
        <Markdown :source="current_md" class="markdown" />
        <h3>Recent Activities</h3>
        <div class="mission-list-container">
          <Mission
            v-for="item in this.missions"
            :key="item.slug"
            :mission="item"
            :selected="this.mission_slug"
            @click="selectMission(item)"
          />
        </div>
      </div>
    </section>
    <section class="section-container" id="events" style="width:335px; height:714px;">
      <div class="section-header clipped-medium-backward">
        <img src="/icons/events-icon.svg" />
        <h1>The Game</h1>
      </div>
      <div class="section-content-container">
        <Markdown :source="events" class="markdown" />
      </div>
    </section>
    <section class="section-container" id="pilots" style="width:470px; height:714px;">
      <div style="height:52px; overflow:hidden;">
        <div class="section-header clipped-medium-backward-pilot">
          <img src="/icons/pilot-icon.svg" />
          <h1>118th House</h1>
        </div>
        <div class="rhombus-back">&nbsp;</div>
      </div>
      <div class="section-content-container">
        <div class="pilot-list-container">
          <Pilot v-for="item in this.pilots" :key="item.slug" :pilot="item" />
        </div>
      </div>
    </section>
  </div>
  <svg
    style="visibility: hidden; position: absolute;"
    width="0"
    height="0"
    xmlns="http://www.w3.org/2000/svg"
    version="1.1"
  >
    <defs>
      <filter id="round">
        <feGaussianBlur in="SourceGraphic" stdDeviation="5" result="blur" />
        <feColorMatrix
          in="blur"
          mode="matrix"
          values="1 0 0 0 0  0 1 0 0 0  0 0 1 0 0  0 0 0 19 -5"
          result="goo"
        />
        <feComposite in="SourceGraphic" in2="goo" operator="atop" />
      </filter>
    </defs>
  </svg>
  <audio autoplay>
    <source src="/startup.ogg" type="audio/ogg" />
  </audio>
  <Footer/>
</template>

<script>
import Header from './components/layout/Header.vue';
import Footer from './components/layout/Footer.vue';
import Mission from './components/Mission.vue';
import Pilot from './components/Pilot.vue';
import Markdown from 'vue3-markdown-it';

export default {
  components: {
    Header,
    Footer,
    Mission,
    Pilot,
    Markdown
  },

  data() {
    return {
      "mission_slug": "001",
      "current_md": "",
      "events": "",
      "missions": [
        {
          "slug": "001",
          "name": "Pick your player.",
          "status": "start"
        },
      ],
      "pilots": [
        {
          "callsign": "Aaron Bean",
          "alias": "Aaron Bean",
          "code": "Points:  22",

          "frame": " Republican",
          "mech": "Florida"
        },
        {
          "callsign": "Abigail Spanberger",
          "alias": "Abigail Spanberger",
          "code": "Points:  19",

          "frame": "Democrat",
          "mech": "Virginia"
        },
        {
          "callsign": "Adam Schiff",
          "alias": "Adam Schiff",
          "code": "Points:  44",

          "frame": "Democrat",
          "mech": "California"
        },
        {
          "callsign": "Warren Davidson",
          "alias": "Warren Davidson",
          "code": "Points:  38",

          "frame": "Republican",
          "mech": "Ohio"
        },
        {
          "callsign": "Wiley Nickel",
          "alias": "Wiley Nickel",
          "code": "Points:  25",

          "frame": "Democrat",
          "mech": "North Carolina"
        },
        {
          "callsign": "William Timmons",
          "alias": "William Timmons",
          "code": "Points:  51",

          "frame": "Republican",
          "mech": "South Carolina"
        },


      ],
      "header": {
        "planet": "United States",
        "year": "2023",
        "system": "Work Dojos",
        "gate": "Congress",
        "ring": "House",
        "headerTitle": "Legislators.Live",
        "headerSubtitle": "Game of Politics",
        "subheaderTitle": "118th US Congress",
        "subheaderSubtitle": "Leaderboard",
      },
      "options":{
        "eventsMarkdownPerMission": true
      }
    }
  },





  created() {
    this.loadMissionMarkdown()
    this.loadEventsMarkdown()
  },

  computed: {

  },

  methods: {
    selectMission(mission) {
      this.mission_slug = mission.slug;
      this.loadMissionMarkdown()
      if(this.options.eventsMarkdownPerMission){
        this.loadEventsMarkdown();
      }
    },
    loadMissionMarkdown() {
      let self = this;
      let md = `/missions/${self.mission_slug}.md`
      var client = new XMLHttpRequest();
      client.open('GET', md);
      client.onreadystatechange = function () {
        self.current_md = client.responseText;
      }
      client.send();
    },
    loadEventsMarkdown() {
      let self = this;
      let md = "";

      if(self.options.eventsMarkdownPerMission){
        md = `/events/${self.mission_slug}.md`
      }
      else {
        md = "/events.md"
      }

      var client = new XMLHttpRequest();
      client.open('GET', md);
      client.onreadystatechange = function () {
        self.events = client.responseText;
      }
      client.send();
    }
  }

}
</script>


<style lang="scss">
#app {
  width: 1600px;
  height: 910px;
  overflow: hidden;
}
</style>