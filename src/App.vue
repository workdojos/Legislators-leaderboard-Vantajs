<template>
  <Header :header="this.header" />
  <div class="content-container">
    <section class="section-container" id="missions" style="width:435px; height:714px;">
      <div class="section-header clipped-medium-backward">
        <img src="/icons/mission-icon.svg" />
        <h1>Mission Log</h1>
      </div>
      <div class="section-content-container">
        <h3>Current Assignment</h3>
        <Markdown :source="current_md" class="markdown" />
        <h3>Mission List</h3>
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
    <section class="section-container" id="events" style="width:435px; height:714px;">
      <div class="section-header clipped-medium-backward">
        <img src="/icons/events-icon.svg" />
        <h1>Events Log</h1>
      </div>
      <div class="section-content-container">
        <Markdown :source="events" class="markdown" />
      </div>
    </section>
    <section class="section-container" id="pilots" style="width:894px; height:714px;">
      <div style="height:52px; overflow:hidden;">
        <div class="section-header clipped-medium-backward-pilot">
          <img src="/icons/pilot-icon.svg" />
          <h1>Pilot Roster</h1>
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
          "name": "Bug-Hunt",
          "status": "start"
        },
      ],
      "pilots": [
        {
          "callsign": "Abigail Spanberger",
          "alias": "Abigail Spanberger",
          "code": "Points:  19",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Virginia"
        },
        {
          "callsign": "Adam Schiff",
          "alias": "Adam Schiff",
          "code": "Points:  44",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "California"
        },
        {
          "callsign": "Adrian Smith",
          "alias": "Adrian Smith",
          "code": "Points:  43",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Nebraska"
        },
        {
          "callsign": "Adriano Espaillat",
          "alias": "Adriano Espaillat",
          "code": "Points:  38",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "New York"
        },
        {
          "callsign": "Al Green",
          "alias": "Al Green",
          "code": "Points:  4",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Texas"
        },
        {
          "callsign": "Alexander Mooney",
          "alias": "Alexander Mooney",
          "code": "Points:  29",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "West Virginia"
        },
        {
          "callsign": "Alexandria Ocasio-Cortez",
          "alias": "Alexandria Ocasio-Cortez",
          "code": "Points:  45",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "New York"
        },
        {
          "callsign": "Alma Adams",
          "alias": "Alma Adams",
          "code": "Points:  19",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "North Carolina"
        },
        {
          "callsign": "Ami Bera",
          "alias": "Ami Bera",
          "code": "Points:  48",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "California"
        },
        {
          "callsign": "André Carson",
          "alias": "André Carson",
          "code": "Points:  28",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Indiana"
        },
        {
          "callsign": "Andrea Salinas",
          "alias": "Andrea Salinas",
          "code": "Points:  26",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Oregon"
        },
        {
          "callsign": "Andrew Clyde",
          "alias": "Andrew Clyde",
          "code": "Points:  17",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Georgia"
        },
        {
          "callsign": "Andrew Garbarino",
          "alias": "Andrew Garbarino",
          "code": "Points:  37",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "New York"
        },
        {
          "callsign": "Andrew Harris",
          "alias": "Andrew Harris",
          "code": "Points:  4",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Maryland"
        },
        {
          "callsign": "Andrew Kim",
          "alias": "Andrew Kim",
          "code": "Points:  4",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "New Jersey"
        },
        {
          "callsign": "Andy Barr",
          "alias": "Andy Barr",
          "code": "Points:  6",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Kentucky"
        },
        {
          "callsign": "Andy Biggs",
          "alias": "Andy Biggs",
          "code": "Points:  36",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Arizona"
        },
        {
          "callsign": "Andy Ogles",
          "alias": "Andy Ogles",
          "code": "Points:  16",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Tennessee"
        },
        {
          "callsign": "Angie Craig",
          "alias": "Angie Craig",
          "code": "Points:  4",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Minnesota"
        },
        {
          "callsign": "Ann Wagner",
          "alias": "Ann Wagner",
          "code": "Points:  16",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Missouri"
        },
        {
          "callsign": "Anna Eshoo",
          "alias": "Anna Eshoo",
          "code": "Points:  59",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "California"
        },
        {
          "callsign": "Anna Paulina Luna",
          "alias": "Anna Paulina Luna",
          "code": "Points:  27",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Florida"
        },
        {
          "callsign": "Annie Kuster",
          "alias": "Annie Kuster",
          "code": "Points:  5",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "New Hampshire"
        },
        {
          "callsign": "Anthony D'Esposito",
          "alias": "Anthony D'Esposito",
          "code": "Points:  31",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "New York"
        },
        {
          "callsign": "Ashley Hinson",
          "alias": "Ashley Hinson",
          "code": "Points:  23",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Iowa"
        },
        {
          "callsign": "August Pfluger",
          "alias": "August Pfluger",
          "code": "Points:  28",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Texas"
        },
        {
          "callsign": "Aumua Amata Radewagen",
          "alias": "Aumua Amata Radewagen",
          "code": "Points:  4",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "American Samoa"
        },
        {
          "callsign": "Austin Scott",
          "alias": "Austin Scott",
          "code": "Points:  36",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Georgia"
        },
        {
          "callsign": "Ayanna Pressley",
          "alias": "Ayanna Pressley",
          "code": "Points:  50",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Massachusetts"
        },
        {
          "callsign": "Barbara Lee",
          "alias": "Barbara Lee",
          "code": "Points:  5",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "California"
        },
        {
          "callsign": "Barry Loudermilk",
          "alias": "Barry Loudermilk",
          "code": "Points:  2",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Georgia"
        },
        {
          "callsign": "Barry Moore",
          "alias": "Barry Moore",
          "code": "Points:  3",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Alabama"
        },
        {
          "callsign": "Becca Balint",
          "alias": "Becca Balint",
          "code": "Points:  22",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Vermont"
        },
        {
          "callsign": "Benjamin Lee Cline",
          "alias": "Benjamin Lee Cline",
          "code": "Points:  59",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Virginia"
        },
        {
          "callsign": "Bennie Thompson",
          "alias": "Bennie Thompson",
          "code": "Points:  25",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Mississippi"
        },
        {
          "callsign": "Beth Van Duyne",
          "alias": "Beth Van Duyne",
          "code": "Points:  6",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Texas"
        },
        {
          "callsign": "Betty McCollum",
          "alias": "Betty McCollum",
          "code": "Points:  39",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Minnesota"
        },
        {
          "callsign": "Bill Foster",
          "alias": "Bill Foster",
          "code": "Points:  22",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Illinois"
        },
        {
          "callsign": "Bill Huizenga",
          "alias": "Bill Huizenga",
          "code": "Points:  57",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Michigan"
        },
        {
          "callsign": "Bill Johnson",
          "alias": "Bill Johnson",
          "code": "Points:  38",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Ohio"
        },
        {
          "callsign": "Bill Keating",
          "alias": "Bill Keating",
          "code": "Points:  41",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Massachusetts"
        },
        {
          "callsign": "Bill Pascrell",
          "alias": "Bill Pascrell",
          "code": "Points:  48",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "New Jersey"
        },
        {
          "callsign": "Bill Posey",
          "alias": "Bill Posey",
          "code": "Points:  4",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Florida"
        },
        {
          "callsign": "Blaine Luetkemeyer",
          "alias": "Blaine Luetkemeyer",
          "code": "Points:  57",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Missouri"
        },
        {
          "callsign": "Blake Moore",
          "alias": "Blake Moore",
          "code": "Points:  18",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Utah"
        },
        {
          "callsign": "Bob Good",
          "alias": "Bob Good",
          "code": "Points:  38",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Virginia"
        },
        {
          "callsign": "Bob Latta",
          "alias": "Bob Latta",
          "code": "Points:  34",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Ohio"
        },
        {
          "callsign": "Bonnie Watson Coleman",
          "alias": "Bonnie Watson Coleman",
          "code": "Points:  19",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "New Jersey"
        },
        {
          "callsign": "Brad Finstad",
          "alias": "Brad Finstad",
          "code": "Points:  32",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Minnesota"
        },
        {
          "callsign": "Brad Schneider",
          "alias": "Brad Schneider",
          "code": "Points:  53",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Illinois"
        },
        {
          "callsign": "Brad Sherman",
          "alias": "Brad Sherman",
          "code": "Points:  58",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "California"
        },
        {
          "callsign": "Brad Wenstrup",
          "alias": "Brad Wenstrup",
          "code": "Points:  27",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Ohio"
        },
        {
          "callsign": "Brandon Williams",
          "alias": "Brandon Williams",
          "code": "Points:  1",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "New York"
        },
        {
          "callsign": "Brendan Boyle",
          "alias": "Brendan Boyle",
          "code": "Points:  1",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Pennsylvania"
        },
        {
          "callsign": "Brett Guthrie",
          "alias": "Brett Guthrie",
          "code": "Points:  24",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Kentucky"
        },
        {
          "callsign": "Brian Babin",
          "alias": "Brian Babin",
          "code": "Points:  5",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Texas"
        },
        {
          "callsign": "Brian Fitzpatrick",
          "alias": "Brian Fitzpatrick",
          "code": "Points:  10",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Pennsylvania"
        },
        {
          "callsign": "Brian Higgins",
          "alias": "Brian Higgins",
          "code": "Points:  4",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "New York"
        },
        {
          "callsign": "Brian Mast",
          "alias": "Brian Mast",
          "code": "Points:  20",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Florida"
        },
        {
          "callsign": "Brittany Pettersen",
          "alias": "Brittany Pettersen",
          "code": "Points:  24",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Colorado"
        },
        {
          "callsign": "Bruce Westerman",
          "alias": "Bruce Westerman",
          "code": "Points:  24",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Arkansas"
        },
        {
          "callsign": "Bryan Steil",
          "alias": "Bryan Steil",
          "code": "Points:  46",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Wisconsin"
        },
        {
          "callsign": "Burgess Owens",
          "alias": "Burgess Owens",
          "code": "Points:  43",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Utah"
        },
        {
          "callsign": "Byron Donalds",
          "alias": "Byron Donalds",
          "code": "Points:  35",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Florida"
        },
        {
          "callsign": "Carlos Gimenez",
          "alias": "Carlos Gimenez",
          "code": "Points:  46",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Florida"
        },
        {
          "callsign": "Carol Miller",
          "alias": "Carol Miller",
          "code": "Points:  47",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "West Virginia"
        },
        {
          "callsign": "Cathy McMorris Rodgers",
          "alias": "Cathy McMorris Rodgers",
          "code": "Points:  7",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Washington"
        },
        {
          "callsign": "Charles J. Fleischmann",
          "alias": "Charles J. Fleischmann",
          "code": "Points:  59",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Tennessee"
        },
        {
          "callsign": "Chellie Pingree",
          "alias": "Chellie Pingree",
          "code": "Points:  12",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Maine"
        },
        {
          "callsign": "Chip Roy",
          "alias": "Chip Roy",
          "code": "Points:  50",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Texas"
        },
        {
          "callsign": "Chris Pappas",
          "alias": "Chris Pappas",
          "code": "Points:  42",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "New Hampshire"
        },
        {
          "callsign": "Chris Smith",
          "alias": "Chris Smith",
          "code": "Points:  40",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "New Jersey"
        },
        {
          "callsign": "Chris Stewart",
          "alias": "Chris Stewart",
          "code": "Points:  36",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Utah"
        },
        {
          "callsign": "Chrissy Houlahan",
          "alias": "Chrissy Houlahan",
          "code": "Points:  37",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Pennsylvania"
        },
        {
          "callsign": "Christopher Deluzio",
          "alias": "Christopher Deluzio",
          "code": "Points:  37",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Pennsylvania"
        },
        {
          "callsign": "Chuck Edwards",
          "alias": "Chuck Edwards",
          "code": "Points:  0",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "North Carolina"
        },
        {
          "callsign": "Claudia Tenney",
          "alias": "Claudia Tenney",
          "code": "Points:  30",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "New York"
        },
        {
          "callsign": "Clay Higgins",
          "alias": "Clay Higgins",
          "code": "Points:  9",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Louisiana"
        },
        {
          "callsign": "Cliff Bentz",
          "alias": "Cliff Bentz",
          "code": "Points:  23",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Oregon"
        },
        {
          "callsign": "Colin Allred",
          "alias": "Colin Allred",
          "code": "Points:  59",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Texas"
        },
        {
          "callsign": "Cori Bush",
          "alias": "Cori Bush",
          "code": "Points:  3",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Missouri"
        },
        {
          "callsign": "Cory Mills",
          "alias": "Cory Mills",
          "code": "Points:  21",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Florida"
        },
        {
          "callsign": "D. Adam Smith",
          "alias": "D. Adam Smith",
          "code": "Points:  45",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Washington"
        },
        {
          "callsign": "Dale Strong",
          "alias": "Dale Strong",
          "code": "Points:  10",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Alabama"
        },
        {
          "callsign": "Dan Bishop",
          "alias": "Dan Bishop",
          "code": "Points:  38",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "North Carolina"
        },
        {
          "callsign": "Dan Kildee",
          "alias": "Dan Kildee",
          "code": "Points:  45",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Michigan"
        },
        {
          "callsign": "Dan Meuser",
          "alias": "Dan Meuser",
          "code": "Points:  29",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Pennsylvania"
        },
        {
          "callsign": "Dan Newhouse",
          "alias": "Dan Newhouse",
          "code": "Points:  34",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Washington"
        },
        {
          "callsign": "Daniel Crenshaw",
          "alias": "Daniel Crenshaw",
          "code": "Points:  0",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Texas"
        },
        {
          "callsign": "Daniel Goldman",
          "alias": "Daniel Goldman",
          "code": "Points:  0",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "New York"
        },
        {
          "callsign": "Daniel Webster",
          "alias": "Daniel Webster",
          "code": "Points:  36",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Florida"
        },
        {
          "callsign": "Danny K. Davis",
          "alias": "Danny K. Davis",
          "code": "Points:  59",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Illinois"
        },
        {
          "callsign": "Darin LaHood",
          "alias": "Darin LaHood",
          "code": "Points:  11",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Illinois"
        },
        {
          "callsign": "Darrell Issa",
          "alias": "Darrell Issa",
          "code": "Points:  7",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "California"
        },
        {
          "callsign": "Darren Soto",
          "alias": "Darren Soto",
          "code": "Points:  57",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Florida"
        },
        {
          "callsign": "David G. Valadao",
          "alias": "David G. Valadao",
          "code": "Points:  2",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "California"
        },
        {
          "callsign": "David Joyce",
          "alias": "David Joyce",
          "code": "Points:  7",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Ohio"
        },
        {
          "callsign": "David Kustoff",
          "alias": "David Kustoff",
          "code": "Points:  1",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Tennessee"
        },
        {
          "callsign": "David N. Cicilline",
          "alias": "David N. Cicilline",
          "code": "Points:  13",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Rhode Island"
        },
        {
          "callsign": "David Rouzer",
          "alias": "David Rouzer",
          "code": "Points:  4",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "North Carolina"
        },
        {
          "callsign": "David Schweikert",
          "alias": "David Schweikert",
          "code": "Points:  57",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Arizona"
        },
        {
          "callsign": "David Scott",
          "alias": "David Scott",
          "code": "Points:  18",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Georgia"
        },
        {
          "callsign": "David Trone",
          "alias": "David Trone",
          "code": "Points:  26",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Maryland"
        },
        {
          "callsign": "Dean Phillips",
          "alias": "Dean Phillips",
          "code": "Points:  18",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Minnesota"
        },
        {
          "callsign": "Debbie Dingell",
          "alias": "Debbie Dingell",
          "code": "Points:  17",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Michigan"
        },
        {
          "callsign": "Debbie Lesko",
          "alias": "Debbie Lesko",
          "code": "Points:  6",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Arizona"
        },
        {
          "callsign": "Debbie Wasserman Schultz",
          "alias": "Debbie Wasserman Schultz",
          "code": "Points:  29",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Florida"
        },
        {
          "callsign": "Deborah Ross",
          "alias": "Deborah Ross",
          "code": "Points:  36",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "North Carolina"
        },
        {
          "callsign": "Delia Ramirez",
          "alias": "Delia Ramirez",
          "code": "Points:  35",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Illinois"
        },
        {
          "callsign": "Derek Kilmer",
          "alias": "Derek Kilmer",
          "code": "Points:  5",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Washington"
        },
        {
          "callsign": "Derrick Van Orden",
          "alias": "Derrick Van Orden",
          "code": "Points:  12",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Wisconsin"
        },
        {
          "callsign": "Diana DeGette",
          "alias": "Diana DeGette",
          "code": "Points:  8",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Colorado"
        },
        {
          "callsign": "Diana Harshbarger",
          "alias": "Diana Harshbarger",
          "code": "Points:  28",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Tennessee"
        },
        {
          "callsign": "Dina Titus",
          "alias": "Dina Titus",
          "code": "Points:  51",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Nevada"
        },
        {
          "callsign": "Don Bacon",
          "alias": "Don Bacon",
          "code": "Points:  35",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Nebraska"
        },
        {
          "callsign": "Donald Davis",
          "alias": "Donald Davis",
          "code": "Points:  36",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "North Carolina"
        },
        {
          "callsign": "Donald Norcross",
          "alias": "Donald Norcross",
          "code": "Points:  14",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "New Jersey"
        },
        {
          "callsign": "Donald Payne Jr.",
          "alias": "Donald Payne Jr.",
          "code": "Points:  18",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "New Jersey"
        },
        {
          "callsign": "Donald Sternoff Beyer Jr.",
          "alias": "Donald Sternoff Beyer Jr.",
          "code": "Points:  22",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Virginia"
        },
        {
          "callsign": "Doris Matsui",
          "alias": "Doris Matsui",
          "code": "Points:  33",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "California"
        },
        {
          "callsign": "Doug LaMalfa",
          "alias": "Doug LaMalfa",
          "code": "Points:  45",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "California"
        },
        {
          "callsign": "Doug Lamborn",
          "alias": "Doug Lamborn",
          "code": "Points:  55",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Colorado"
        },
        {
          "callsign": "Drew Ferguson",
          "alias": "Drew Ferguson",
          "code": "Points:  42",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Georgia"
        },
        {
          "callsign": "Dusty Johnson",
          "alias": "Dusty Johnson",
          "code": "Points:  31",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "South Dakota"
        },
        {
          "callsign": "Dutch Ruppersberger",
          "alias": "Dutch Ruppersberger",
          "code": "Points:  51",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Maryland"
        },
        {
          "callsign": "Dwight Evans",
          "alias": "Dwight Evans",
          "code": "Points:  58",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Pennsylvania"
        },
        {
          "callsign": "Earl Blumenauer",
          "alias": "Earl Blumenauer",
          "code": "Points:  56",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Oregon"
        },
        {
          "callsign": "Earl Carter",
          "alias": "Earl Carter",
          "code": "Points:  45",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Georgia"
        },
        {
          "callsign": "Ed Case",
          "alias": "Ed Case",
          "code": "Points:  47",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Hawaii"
        },
        {
          "callsign": "Eleanor Holmes Norton",
          "alias": "Eleanor Holmes Norton",
          "code": "Points:  50",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Non-Voting"
        },
        {
          "callsign": "Eli Crane",
          "alias": "Eli Crane",
          "code": "Points:  33",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Arizona"
        },
        {
          "callsign": "Elise Stefanik",
          "alias": "Elise Stefanik",
          "code": "Points:  27",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "New York"
        },
        {
          "callsign": "Elissa Slotkin",
          "alias": "Elissa Slotkin",
          "code": "Points:  44",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Michigan"
        },
        {
          "callsign": "Emanuel Cleaver",
          "alias": "Emanuel Cleaver",
          "code": "Points:  58",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Missouri"
        },
        {
          "callsign": "Emilia Sykes",
          "alias": "Emilia Sykes",
          "code": "Points:  32",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Ohio"
        },
        {
          "callsign": "Eric Burlison",
          "alias": "Eric Burlison",
          "code": "Points:  55",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Missouri"
        },
        {
          "callsign": "Eric Sorensen",
          "alias": "Eric Sorensen",
          "code": "Points:  5",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Illinois"
        },
        {
          "callsign": "Eric Swalwell",
          "alias": "Eric Swalwell",
          "code": "Points:  25",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "California"
        },
        {
          "callsign": "Erin Houchin",
          "alias": "Erin Houchin",
          "code": "Points:  33",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Indiana"
        },
        {
          "callsign": "Frank Lucas",
          "alias": "Frank Lucas",
          "code": "Points:  44",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Oklahoma"
        },
        {
          "callsign": "Frank Mrvan",
          "alias": "Frank Mrvan",
          "code": "Points:  23",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Indiana"
        },
        {
          "callsign": "Frank Pallone Jr.",
          "alias": "Frank Pallone Jr.",
          "code": "Points:  59",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "New Jersey"
        },
        {
          "callsign": "Frederica S. Wilson",
          "alias": "Frederica S. Wilson",
          "code": "Points:  38",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Florida"
        },
        {
          "callsign": "French Hill",
          "alias": "French Hill",
          "code": "Points:  42",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Arkansas"
        },
        {
          "callsign": "Gabriel Vasquez",
          "alias": "Gabriel Vasquez",
          "code": "Points:  34",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "New Mexico"
        },
        {
          "callsign": "Garret Graves",
          "alias": "Garret Graves",
          "code": "Points:  21",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Louisiana"
        },
        {
          "callsign": "Gary Palmer",
          "alias": "Gary Palmer",
          "code": "Points:  28",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Alabama"
        },
        {
          "callsign": "George Devolder-Santos",
          "alias": "George Devolder-Santos",
          "code": "Points:  26",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "New York"
        },
        {
          "callsign": "Gerald Edward Connolly",
          "alias": "Gerald Edward Connolly",
          "code": "Points:  34",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Virginia"
        },
        {
          "callsign": "Glenn Grothman",
          "alias": "Glenn Grothman",
          "code": "Points:  17",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Wisconsin"
        },
        {
          "callsign": "Glenn Ivey",
          "alias": "Glenn Ivey",
          "code": "Points:  39",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Maryland"
        },
        {
          "callsign": "Glenn Thompson",
          "alias": "Glenn Thompson",
          "code": "Points:  38",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Pennsylvania"
        },
        {
          "callsign": "Grace Meng",
          "alias": "Grace Meng",
          "code": "Points:  21",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "New York"
        },
        {
          "callsign": "Grace Napolitano",
          "alias": "Grace Napolitano",
          "code": "Points:  51",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "California"
        },
        {
          "callsign": "Greg Casar",
          "alias": "Greg Casar",
          "code": "Points:  54",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Texas"
        },
        {
          "callsign": "Greg Landsman",
          "alias": "Greg Landsman",
          "code": "Points:  24",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Ohio"
        },
        {
          "callsign": "Greg Pence",
          "alias": "Greg Pence",
          "code": "Points:  11",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Indiana"
        },
        {
          "callsign": "Greg Stanton",
          "alias": "Greg Stanton",
          "code": "Points:  15",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Arizona"
        },
        {
          "callsign": "Greg Steube",
          "alias": "Greg Steube",
          "code": "Points:  23",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Florida"
        },
        {
          "callsign": "Gregorio Kilili Camacho Sablan",
          "alias": "Gregorio Kilili Camacho Sablan",
          "code": "Points:  42",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Northern Mariana Islands"
        },
        {
          "callsign": "Gregory Murphy",
          "alias": "Gregory Murphy",
          "code": "Points:  5",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "North Carolina"
        },
        {
          "callsign": "Gregory W. Meeks",
          "alias": "Gregory W. Meeks",
          "code": "Points:  5",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "New York"
        },
        {
          "callsign": "Gus M. Bilirakis",
          "alias": "Gus M. Bilirakis",
          "code": "Points:  14",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Florida"
        },
        {
          "callsign": "Guy Reschenthaler",
          "alias": "Guy Reschenthaler",
          "code": "Points:  10",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Pennsylvania"
        },
        {
          "callsign": "Gwen Moore",
          "alias": "Gwen Moore",
          "code": "Points:  32",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Wisconsin"
        },
        {
          "callsign": "H. Morgan Griffith",
          "alias": "H. Morgan Griffith",
          "code": "Points:  22",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Virginia"
        },
        {
          "callsign": "Hakeem Jeffries",
          "alias": "Hakeem Jeffries",
          "code": "Points:  47",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "New York"
        },
        {
          "callsign": "Hal Rogers",
          "alias": "Hal Rogers",
          "code": "Points:  25",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Kentucky"
        },
        {
          "callsign": "Haley Stevens",
          "alias": "Haley Stevens",
          "code": "Points:  47",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Michigan"
        },
        {
          "callsign": "Hank Johnson",
          "alias": "Hank Johnson",
          "code": "Points:  56",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Georgia"
        },
        {
          "callsign": "Harriet Hageman",
          "alias": "Harriet Hageman",
          "code": "Points:  54",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Wyoming"
        },
        {
          "callsign": "Henry Cuellar",
          "alias": "Henry Cuellar",
          "code": "Points:  17",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Texas"
        },
        {
          "callsign": "Hillary Scholten",
          "alias": "Hillary Scholten",
          "code": "Points:  26",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Michigan"
        },
        {
          "callsign": "Ilhan Omar",
          "alias": "Ilhan Omar",
          "code": "Points:  22",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Minnesota"
        },
        {
          "callsign": "Jack Bergman",
          "alias": "Jack Bergman",
          "code": "Points:  24",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Michigan"
        },
        {
          "callsign": "Jacob LaTurner",
          "alias": "Jacob LaTurner",
          "code": "Points:  42",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Kansas"
        },
        {
          "callsign": "Jahana Hayes",
          "alias": "Jahana Hayes",
          "code": "Points:  5",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Connecticut"
        },
        {
          "callsign": "Jake Auchincloss",
          "alias": "Jake Auchincloss",
          "code": "Points:  52",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Massachusetts"
        },
        {
          "callsign": "Jake Ellzey",
          "alias": "Jake Ellzey",
          "code": "Points:  9",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Texas"
        },
        {
          "callsign": "Jamaal Bowman",
          "alias": "Jamaal Bowman",
          "code": "Points:  49",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "New York"
        },
        {
          "callsign": "James Clyburn",
          "alias": "James Clyburn",
          "code": "Points:  15",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "South Carolina"
        },
        {
          "callsign": "James Comer Jr.",
          "alias": "James Comer Jr.",
          "code": "Points:  52",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Kentucky"
        },
        {
          "callsign": "James Moylan",
          "alias": "James Moylan",
          "code": "Points:  45",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Guam"
        },
        {
          "callsign": "Jamie Raskin",
          "alias": "Jamie Raskin",
          "code": "Points:  51",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Maryland"
        },
        {
          "callsign": "Jan Schakowsky",
          "alias": "Jan Schakowsky",
          "code": "Points:  3",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Illinois"
        },
        {
          "callsign": "Jared Evan Moskowitz",
          "alias": "Jared Evan Moskowitz",
          "code": "Points:  17",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Florida"
        },
        {
          "callsign": "Jared Golden",
          "alias": "Jared Golden",
          "code": "Points:  42",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Maine"
        },
        {
          "callsign": "Jared Huffman",
          "alias": "Jared Huffman",
          "code": "Points:  36",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "California"
        },
        {
          "callsign": "Jasmine Crockett",
          "alias": "Jasmine Crockett",
          "code": "Points:  23",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Texas"
        },
        {
          "callsign": "Jason Crow",
          "alias": "Jason Crow",
          "code": "Points:  34",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Colorado"
        },
        {
          "callsign": "Jason Smith",
          "alias": "Jason Smith",
          "code": "Points:  0",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Missouri"
        },
        {
          "callsign": "Jay Obernolte",
          "alias": "Jay Obernolte",
          "code": "Points:  14",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "California"
        },
        {
          "callsign": "Jeff Duncan",
          "alias": "Jeff Duncan",
          "code": "Points:  5",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "South Carolina"
        },
        {
          "callsign": "Jeff Jackson",
          "alias": "Jeff Jackson",
          "code": "Points:  56",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "North Carolina"
        },
        {
          "callsign": "Jeff Van Drew",
          "alias": "Jeff Van Drew",
          "code": "Points:  39",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "New Jersey"
        },
        {
          "callsign": "Jennifer Kiggans",
          "alias": "Jennifer Kiggans",
          "code": "Points:  12",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Virginia"
        },
        {
          "callsign": "Jennifer McClellan",
          "alias": "Jennifer McClellan",
          "code": "Points:  48",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Virginia"
        },
        {
          "callsign": "Jennifer Wexton",
          "alias": "Jennifer Wexton",
          "code": "Points:  23",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Virginia"
        },
        {
          "callsign": "Jerrold Nadler",
          "alias": "Jerrold Nadler",
          "code": "Points:  16",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "New York"
        },
        {
          "callsign": "Jerry Carl",
          "alias": "Jerry Carl",
          "code": "Points:  42",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Alabama"
        },
        {
          "callsign": "Jesus Garcia",
          "alias": "Jesus Garcia",
          "code": "Points:  37",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Illinois"
        },
        {
          "callsign": "Jill Tokuda",
          "alias": "Jill Tokuda",
          "code": "Points:  48",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Hawaii"
        },
        {
          "callsign": "Jim Baird",
          "alias": "Jim Baird",
          "code": "Points:  37",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Indiana"
        },
        {
          "callsign": "Jim Banks",
          "alias": "Jim Banks",
          "code": "Points:  58",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Indiana"
        },
        {
          "callsign": "Jim Costa",
          "alias": "Jim Costa",
          "code": "Points:  11",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "California"
        },
        {
          "callsign": "Jim Himes",
          "alias": "Jim Himes",
          "code": "Points:  58",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Connecticut"
        },
        {
          "callsign": "Jim Jordan",
          "alias": "Jim Jordan",
          "code": "Points:  3",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Ohio"
        },
        {
          "callsign": "Jim McGovern",
          "alias": "Jim McGovern",
          "code": "Points:  52",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Massachusetts"
        },
        {
          "callsign": "Jimmy Gomez",
          "alias": "Jimmy Gomez",
          "code": "Points:  10",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "California"
        },
        {
          "callsign": "Jimmy Panetta",
          "alias": "Jimmy Panetta",
          "code": "Points:  7",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "California"
        },
        {
          "callsign": "Joaquin Castro",
          "alias": "Joaquin Castro",
          "code": "Points:  56",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Texas"
        },
        {
          "callsign": "Jodey Arrington",
          "alias": "Jodey Arrington",
          "code": "Points:  24",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Texas"
        },
        {
          "callsign": "Joe Courtney",
          "alias": "Joe Courtney",
          "code": "Points:  11",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Connecticut"
        },
        {
          "callsign": "Joe Neguse",
          "alias": "Joe Neguse",
          "code": "Points:  58",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Colorado"
        },
        {
          "callsign": "Joe Wilson",
          "alias": "Joe Wilson",
          "code": "Points:  4",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "South Carolina"
        },
        {
          "callsign": "John Carter",
          "alias": "John Carter",
          "code": "Points:  11",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Texas"
        },
        {
          "callsign": "John Curtis",
          "alias": "John Curtis",
          "code": "Points:  52",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Utah"
        },
        {
          "callsign": "John Duarte",
          "alias": "John Duarte",
          "code": "Points:  52",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "California"
        },
        {
          "callsign": "John Garamendi",
          "alias": "John Garamendi",
          "code": "Points:  19",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "California"
        },
        {
          "callsign": "John James",
          "alias": "John James",
          "code": "Points:  27",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Michigan"
        },
        {
          "callsign": "John Joyce",
          "alias": "John Joyce",
          "code": "Points:  33",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Pennsylvania"
        },
        {
          "callsign": "John Larson",
          "alias": "John Larson",
          "code": "Points:  1",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Connecticut"
        },
        {
          "callsign": "John Moolenaar",
          "alias": "John Moolenaar",
          "code": "Points:  42",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Michigan"
        },
        {
          "callsign": "John Rose",
          "alias": "John Rose",
          "code": "Points:  38",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Tennessee"
        },
        {
          "callsign": "John Rutherford",
          "alias": "John Rutherford",
          "code": "Points:  28",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Florida"
        },
        {
          "callsign": "John Sarbanes",
          "alias": "John Sarbanes",
          "code": "Points:  27",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Maryland"
        },
        {
          "callsign": "Jonathan Jackson",
          "alias": "Jonathan Jackson",
          "code": "Points:  6",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Illinois"
        },
        {
          "callsign": "Joseph Morelle",
          "alias": "Joseph Morelle",
          "code": "Points:  57",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "New York"
        },
        {
          "callsign": "Josh Brecheen",
          "alias": "Josh Brecheen",
          "code": "Points:  57",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Oklahoma"
        },
        {
          "callsign": "Josh Gottheimer",
          "alias": "Josh Gottheimer",
          "code": "Points:  35",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "New Jersey"
        },
        {
          "callsign": "Josh Harder",
          "alias": "Josh Harder",
          "code": "Points:  38",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "California"
        },
        {
          "callsign": "Joyce Beatty",
          "alias": "Joyce Beatty",
          "code": "Points:  26",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Ohio"
        },
        {
          "callsign": "Juan Ciscomani",
          "alias": "Juan Ciscomani",
          "code": "Points:  51",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Arizona"
        },
        {
          "callsign": "Juan Vargas",
          "alias": "Juan Vargas",
          "code": "Points:  52",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "California"
        },
        {
          "callsign": "Judy Chu",
          "alias": "Judy Chu",
          "code": "Points:  27",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "California"
        },
        {
          "callsign": "Julia Brownley",
          "alias": "Julia Brownley",
          "code": "Points:  14",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "California"
        },
        {
          "callsign": "Julia Letlow",
          "alias": "Julia Letlow",
          "code": "Points:  7",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Louisiana"
        },
        {
          "callsign": "Kat Cammack",
          "alias": "Kat Cammack",
          "code": "Points:  56",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Florida"
        },
        {
          "callsign": "Katherine Clark",
          "alias": "Katherine Clark",
          "code": "Points:  44",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Massachusetts"
        },
        {
          "callsign": "Kathy Castor",
          "alias": "Kathy Castor",
          "code": "Points:  2",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Florida"
        },
        {
          "callsign": "Kathy Manning",
          "alias": "Kathy Manning",
          "code": "Points:  0",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "North Carolina"
        },
        {
          "callsign": "Katie Porter",
          "alias": "Katie Porter",
          "code": "Points:  10",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "California"
        },
        {
          "callsign": "Kay Granger",
          "alias": "Kay Granger",
          "code": "Points:  47",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Texas"
        },
        {
          "callsign": "Keith Self",
          "alias": "Keith Self",
          "code": "Points:  38",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Texas"
        },
        {
          "callsign": "Kelly Armstrong",
          "alias": "Kelly Armstrong",
          "code": "Points:  25",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "North Dakota"
        },
        {
          "callsign": "Ken Buck",
          "alias": "Ken Buck",
          "code": "Points:  2",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Colorado"
        },
        {
          "callsign": "Ken Calvert",
          "alias": "Ken Calvert",
          "code": "Points:  48",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "California"
        },
        {
          "callsign": "Kevin Hern",
          "alias": "Kevin Hern",
          "code": "Points:  32",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Oklahoma"
        },
        {
          "callsign": "Kevin Kiley",
          "alias": "Kevin Kiley",
          "code": "Points:  19",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "California"
        },
        {
          "callsign": "Kevin McCarthy",
          "alias": "Kevin McCarthy",
          "code": "Points:  55",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "California"
        },
        {
          "callsign": "Kevin Mullin",
          "alias": "Kevin Mullin",
          "code": "Points:  20",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "California"
        },
        {
          "callsign": "Kim Schrier",
          "alias": "Kim Schrier",
          "code": "Points:  40",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Washington"
        },
        {
          "callsign": "Kweisi Mfume",
          "alias": "Kweisi Mfume",
          "code": "Points:  27",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Maryland"
        },
        {
          "callsign": "Lance Gooden",
          "alias": "Lance Gooden",
          "code": "Points:  21",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Texas"
        },
        {
          "callsign": "Larry Bucshon",
          "alias": "Larry Bucshon",
          "code": "Points:  33",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Indiana"
        },
        {
          "callsign": "Laurel Lee",
          "alias": "Laurel Lee",
          "code": "Points:  41",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Florida"
        },
        {
          "callsign": "Lauren Boebert",
          "alias": "Lauren Boebert",
          "code": "Points:  24",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Colorado"
        },
        {
          "callsign": "Lauren Underwood",
          "alias": "Lauren Underwood",
          "code": "Points:  36",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Illinois"
        },
        {
          "callsign": "Linda Sánchez",
          "alias": "Linda Sánchez",
          "code": "Points:  55",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "California"
        },
        {
          "callsign": "Lisa Blunt Rochester",
          "alias": "Lisa Blunt Rochester",
          "code": "Points:  11",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Delaware"
        },
        {
          "callsign": "Lisa McClain",
          "alias": "Lisa McClain",
          "code": "Points:  14",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Michigan"
        },
        {
          "callsign": "Lizzie Pannill Fletcher",
          "alias": "Lizzie Pannill Fletcher",
          "code": "Points:  21",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Texas"
        },
        {
          "callsign": "Lloyd Doggett",
          "alias": "Lloyd Doggett",
          "code": "Points:  23",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Texas"
        },
        {
          "callsign": "Lloyd Smucker",
          "alias": "Lloyd Smucker",
          "code": "Points:  56",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Pennsylvania"
        },
        {
          "callsign": "Lois Frankel",
          "alias": "Lois Frankel",
          "code": "Points:  12",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Florida"
        },
        {
          "callsign": "Lori Chavez-DeRemer",
          "alias": "Lori Chavez-DeRemer",
          "code": "Points:  34",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Oregon"
        },
        {
          "callsign": "Lori Trahan",
          "alias": "Lori Trahan",
          "code": "Points:  26",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Massachusetts"
        },
        {
          "callsign": "Lou Correa",
          "alias": "Lou Correa",
          "code": "Points:  55",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "California"
        },
        {
          "callsign": "Lucy McBath",
          "alias": "Lucy McBath",
          "code": "Points:  41",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Georgia"
        },
        {
          "callsign": "Madeleine Dean",
          "alias": "Madeleine Dean",
          "code": "Points:  51",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Pennsylvania"
        },
        {
          "callsign": "Marc Veasey",
          "alias": "Marc Veasey",
          "code": "Points:  40",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Texas"
        },
        {
          "callsign": "Marcus Molinaro",
          "alias": "Marcus Molinaro",
          "code": "Points:  30",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "New York"
        },
        {
          "callsign": "Marcy Kaptur",
          "alias": "Marcy Kaptur",
          "code": "Points:  29",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Ohio"
        },
        {
          "callsign": "Maria Elvira Salazar",
          "alias": "Maria Elvira Salazar",
          "code": "Points:  2",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Florida"
        },
        {
          "callsign": "Mariannette Miller-Meeks",
          "alias": "Mariannette Miller-Meeks",
          "code": "Points:  23",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Iowa"
        },
        {
          "callsign": "Marie Gluesenkamp Pérez",
          "alias": "Marie Gluesenkamp Pérez",
          "code": "Points:  34",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Washington"
        },
        {
          "callsign": "Marilyn Strickland",
          "alias": "Marilyn Strickland",
          "code": "Points:  27",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Washington"
        },
        {
          "callsign": "Mario Diaz-Balart",
          "alias": "Mario Diaz-Balart",
          "code": "Points:  36",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Florida"
        },
        {
          "callsign": "Marjorie Taylor Greene",
          "alias": "Marjorie Taylor Greene",
          "code": "Points:  56",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Georgia"
        },
        {
          "callsign": "Mark Alford",
          "alias": "Mark Alford",
          "code": "Points:  2",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Missouri"
        },
        {
          "callsign": "Mark Amodei",
          "alias": "Mark Amodei",
          "code": "Points:  30",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Nevada"
        },
        {
          "callsign": "Mark DeSaulnier",
          "alias": "Mark DeSaulnier",
          "code": "Points:  59",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "California"
        },
        {
          "callsign": "Mark Green",
          "alias": "Mark Green",
          "code": "Points:  58",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Tennessee"
        },
        {
          "callsign": "Mark Pocan",
          "alias": "Mark Pocan",
          "code": "Points:  22",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Wisconsin"
        },
        {
          "callsign": "Mark Takano",
          "alias": "Mark Takano",
          "code": "Points:  37",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "California"
        },
        {
          "callsign": "Mary Gay Scanlon",
          "alias": "Mary Gay Scanlon",
          "code": "Points:  49",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Pennsylvania"
        },
        {
          "callsign": "Mary Miller",
          "alias": "Mary Miller",
          "code": "Points:  27",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Illinois"
        },
        {
          "callsign": "Mary Peltola",
          "alias": "Mary Peltola",
          "code": "Points:  15",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Alaska"
        },
        {
          "callsign": "Matt Cartwright",
          "alias": "Matt Cartwright",
          "code": "Points:  5",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Pennsylvania"
        },
        {
          "callsign": "Matt Gaetz",
          "alias": "Matt Gaetz",
          "code": "Points:  19",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Florida"
        },
        {
          "callsign": "Matt Rosendale",
          "alias": "Matt Rosendale",
          "code": "Points:  20",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Montana"
        },
        {
          "callsign": "Max Miller",
          "alias": "Max Miller",
          "code": "Points:  57",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Ohio"
        },
        {
          "callsign": "Maxine Waters",
          "alias": "Maxine Waters",
          "code": "Points:  27",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "California"
        },
        {
          "callsign": "Maxwell Alejandro Frost",
          "alias": "Maxwell Alejandro Frost",
          "code": "Points:  27",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Florida"
        },
        {
          "callsign": "Melanie Ann Stansbury",
          "alias": "Melanie Ann Stansbury",
          "code": "Points:  20",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "New Mexico"
        },
        {
          "callsign": "Michael C. Burgess",
          "alias": "Michael C. Burgess",
          "code": "Points:  46",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Texas"
        },
        {
          "callsign": "Michael Cloud",
          "alias": "Michael Cloud",
          "code": "Points:  10",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Texas"
        },
        {
          "callsign": "Michael Guest",
          "alias": "Michael Guest",
          "code": "Points:  36",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Mississippi"
        },
        {
          "callsign": "Michael K. Simpson",
          "alias": "Michael K. Simpson",
          "code": "Points:  46",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Idaho"
        },
        {
          "callsign": "Michael Lawler",
          "alias": "Michael Lawler",
          "code": "Points:  42",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "New York"
        },
        {
          "callsign": "Michael McCaul",
          "alias": "Michael McCaul",
          "code": "Points:  28",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Texas"
        },
        {
          "callsign": "Michael Turner",
          "alias": "Michael Turner",
          "code": "Points:  55",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Ohio"
        },
        {
          "callsign": "Michael Waltz",
          "alias": "Michael Waltz",
          "code": "Points:  58",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Florida"
        },
        {
          "callsign": "Michelle Fischbach",
          "alias": "Michelle Fischbach",
          "code": "Points:  55",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Minnesota"
        },
        {
          "callsign": "Michelle Steel",
          "alias": "Michelle Steel",
          "code": "Points:  15",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "California"
        },
        {
          "callsign": "Mike Bost",
          "alias": "Mike Bost",
          "code": "Points:  2",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Illinois"
        },
        {
          "callsign": "Mike Carey",
          "alias": "Mike Carey",
          "code": "Points:  55",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Ohio"
        },
        {
          "callsign": "Mike Collins",
          "alias": "Mike Collins",
          "code": "Points:  27",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Georgia"
        },
        {
          "callsign": "Mike Ezell",
          "alias": "Mike Ezell",
          "code": "Points:  2",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Mississippi"
        },
        {
          "callsign": "Mike Flood",
          "alias": "Mike Flood",
          "code": "Points:  17",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Nebraska"
        },
        {
          "callsign": "Mike Gallagher",
          "alias": "Mike Gallagher",
          "code": "Points:  17",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Wisconsin"
        },
        {
          "callsign": "Mike Garcia",
          "alias": "Mike Garcia",
          "code": "Points:  59",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "California"
        },
        {
          "callsign": "Mike Johnson",
          "alias": "Mike Johnson",
          "code": "Points:  11",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Louisiana"
        },
        {
          "callsign": "Mike Kelly",
          "alias": "Mike Kelly",
          "code": "Points:  23",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Pennsylvania"
        },
        {
          "callsign": "Mike Levin",
          "alias": "Mike Levin",
          "code": "Points:  7",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "California"
        },
        {
          "callsign": "Mike Quigley",
          "alias": "Mike Quigley",
          "code": "Points:  32",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Illinois"
        },
        {
          "callsign": "Mike Rogers",
          "alias": "Mike Rogers",
          "code": "Points:  35",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Alabama"
        },
        {
          "callsign": "Mike Thompson",
          "alias": "Mike Thompson",
          "code": "Points:  31",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "California"
        },
        {
          "callsign": "Mikie Sherrill",
          "alias": "Mikie Sherrill",
          "code": "Points:  5",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "New Jersey"
        },
        {
          "callsign": "Monica De La Cruz",
          "alias": "Monica De La Cruz",
          "code": "Points:  32",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Texas"
        },
        {
          "callsign": "Morgan Luttrell",
          "alias": "Morgan Luttrell",
          "code": "Points:  19",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Texas"
        },
        {
          "callsign": "Morgan McGarvey",
          "alias": "Morgan McGarvey",
          "code": "Points:  27",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Kentucky"
        },
        {
          "callsign": "Nancy Mace",
          "alias": "Nancy Mace",
          "code": "Points:  6",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "South Carolina"
        },
        {
          "callsign": "Nancy Pelosi",
          "alias": "Nancy Pelosi",
          "code": "Points:  28",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "California"
        },
        {
          "callsign": "Nanette Barragán",
          "alias": "Nanette Barragán",
          "code": "Points:  50",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "California"
        },
        {
          "callsign": "Nathaniel Moran",
          "alias": "Nathaniel Moran",
          "code": "Points:  50",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Texas"
        },
        {
          "callsign": "Neal Dunn",
          "alias": "Neal Dunn",
          "code": "Points:  42",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Florida"
        },
        {
          "callsign": "Nicholas A. Langworthy",
          "alias": "Nicholas A. Langworthy",
          "code": "Points:  55",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "New York"
        },
        {
          "callsign": "Nicholas J. LaLota",
          "alias": "Nicholas J. LaLota",
          "code": "Points:  28",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "New York"
        },
        {
          "callsign": "Nicole Malliotakis",
          "alias": "Nicole Malliotakis",
          "code": "Points:  28",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "New York"
        },
        {
          "callsign": "Nikema Williams",
          "alias": "Nikema Williams",
          "code": "Points:  2",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Georgia"
        },
        {
          "callsign": "Nikki Budzinski",
          "alias": "Nikki Budzinski",
          "code": "Points:  14",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Illinois"
        },
        {
          "callsign": "Norma Torres",
          "alias": "Norma Torres",
          "code": "Points:  17",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "California"
        },
        {
          "callsign": "Nydia Velazquez",
          "alias": "Nydia Velazquez",
          "code": "Points:  42",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "New"
        },
        {
          "callsign": "Pat Fallon",
          "alias": "Pat Fallon",
          "code": "Points:  23",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Texas"
        },
        {
          "callsign": "Pat Ryan",
          "alias": "Pat Ryan",
          "code": "Points:  8",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "New"
        },
        {
          "callsign": "Patrick T. McHenry",
          "alias": "Patrick T. McHenry",
          "code": "Points:  41",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "North Carolina"
        },
        {
          "callsign": "Paul Gosar",
          "alias": "Paul Gosar",
          "code": "Points:  34",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Arizona"
        },
        {
          "callsign": "Paul Tonko",
          "alias": "Paul Tonko",
          "code": "Points:  52",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "New York"
        },
        {
          "callsign": "Pete Aguilar",
          "alias": "Pete Aguilar",
          "code": "Points:  15",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "California"
        },
        {
          "callsign": "Pete Sessions",
          "alias": "Pete Sessions",
          "code": "Points:  45",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Texas"
        },
        {
          "callsign": "Pete Stauber",
          "alias": "Pete Stauber",
          "code": "Points:  26",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Minnesota"
        },
        {
          "callsign": "Pramila Jayapal",
          "alias": "Pramila Jayapal",
          "code": "Points:  36",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Washington"
        },
        {
          "callsign": "Raja Krishnamoorthi",
          "alias": "Raja Krishnamoorthi",
          "code": "Points:  29",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Illinois"
        },
        {
          "callsign": "Ralph Norman",
          "alias": "Ralph Norman",
          "code": "Points:  45",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "South Carolina"
        },
        {
          "callsign": "Randy Feenstra",
          "alias": "Randy Feenstra",
          "code": "Points:  18",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Iowa"
        },
        {
          "callsign": "Randy Weber",
          "alias": "Randy Weber",
          "code": "Points:  3",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Texas"
        },
        {
          "callsign": "Rashida Tlaib",
          "alias": "Rashida Tlaib",
          "code": "Points:  28",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Michigan"
        },
        {
          "callsign": "Raúl Grijalva",
          "alias": "Raúl Grijalva",
          "code": "Points:  59",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Arizona"
        },
        {
          "callsign": "Raul Ruiz",
          "alias": "Raul Ruiz",
          "code": "Points:  4",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "California"
        },
        {
          "callsign": "Rich McCormick",
          "alias": "Rich McCormick",
          "code": "Points:  42",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Georgia"
        },
        {
          "callsign": "Richard Hudson",
          "alias": "Richard Hudson",
          "code": "Points:  56",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "North Carolina"
        },
        {
          "callsign": "Richard Neal",
          "alias": "Richard Neal",
          "code": "Points:  19",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Massachusetts"
        },
        {
          "callsign": "Rick Allen",
          "alias": "Rick Allen",
          "code": "Points:  43",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Georgia"
        },
        {
          "callsign": "Rick Crawford",
          "alias": "Rick Crawford",
          "code": "Points:  20",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Arkansas"
        },
        {
          "callsign": "Rick Larsen",
          "alias": "Rick Larsen",
          "code": "Points:  24",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Washington"
        },
        {
          "callsign": "Ritchie Torres",
          "alias": "Ritchie Torres",
          "code": "Points:  28",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "New York"
        },
        {
          "callsign": "Ro Khanna",
          "alias": "Ro Khanna",
          "code": "Points:  56",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "California"
        },
        {
          "callsign": "Robert Aderholt",
          "alias": "Robert Aderholt",
          "code": "Points:  34",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Alabama"
        },
        {
          "callsign": "Robert C. Scott",
          "alias": "Robert C. Scott",
          "code": "Points:  19",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Virginia"
        },
        {
          "callsign": "Robert Garcia",
          "alias": "Robert Garcia",
          "code": "Points:  21",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "California"
        },
        {
          "callsign": "Robert J. Wittman",
          "alias": "Robert J. Wittman",
          "code": "Points:  22",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Virginia"
        },
        {
          "callsign": "Robert Menendez Jr.",
          "alias": "Robert Menendez Jr.",
          "code": "Points:  45",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "New Jersey"
        },
        {
          "callsign": "Robin Kelly",
          "alias": "Robin Kelly",
          "code": "Points:  5",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Illinois"
        },
        {
          "callsign": "Roger Williams",
          "alias": "Roger Williams",
          "code": "Points:  11",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Texas"
        },
        {
          "callsign": "Ron Estes",
          "alias": "Ron Estes",
          "code": "Points:  28",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Kansas"
        },
        {
          "callsign": "Ronny L. Jackson",
          "alias": "Ronny L. Jackson",
          "code": "Points:  16",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Texas"
        },
        {
          "callsign": "Rosa L. DeLauro",
          "alias": "Rosa L. DeLauro",
          "code": "Points:  34",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Connecticut"
        },
        {
          "callsign": "Ruben Gallego",
          "alias": "Ruben Gallego",
          "code": "Points:  16",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Arizona"
        },
        {
          "callsign": "Rudy Yakym",
          "alias": "Rudy Yakym",
          "code": "Points:  13",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Indiana"
        },
        {
          "callsign": "Russ Fulcher",
          "alias": "Russ Fulcher",
          "code": "Points:  6",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Idaho"
        },
        {
          "callsign": "Russell Fry",
          "alias": "Russell Fry",
          "code": "Points:  36",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "South Carolina"
        },
        {
          "callsign": "Ryan Zinke",
          "alias": "Ryan Zinke",
          "code": "Points:  41",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Montana"
        },
        {
          "callsign": "Salud Carbajal",
          "alias": "Salud Carbajal",
          "code": "Points:  34",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "California"
        },
        {
          "callsign": "Sam Graves",
          "alias": "Sam Graves",
          "code": "Points:  39",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Missouri"
        },
        {
          "callsign": "Sanford Bishop Jr.",
          "alias": "Sanford Bishop Jr.",
          "code": "Points:  29",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Georgia"
        },
        {
          "callsign": "Sara Jacobs",
          "alias": "Sara Jacobs",
          "code": "Points:  43",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "California"
        },
        {
          "callsign": "Scott DesJarlais",
          "alias": "Scott DesJarlais",
          "code": "Points:  35",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Tennessee"
        },
        {
          "callsign": "Scott Fitzgerald",
          "alias": "Scott Fitzgerald",
          "code": "Points:  57",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Wisconsin"
        },
        {
          "callsign": "Scott Franklin",
          "alias": "Scott Franklin",
          "code": "Points:  8",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Florida"
        },
        {
          "callsign": "Scott Perry",
          "alias": "Scott Perry",
          "code": "Points:  44",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Pennsylvania"
        },
        {
          "callsign": "Scott Peters",
          "alias": "Scott Peters",
          "code": "Points:  13",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "California"
        },
        {
          "callsign": "Sean Casten",
          "alias": "Sean Casten",
          "code": "Points:  35",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Illinois"
        },
        {
          "callsign": "Seth Magaziner",
          "alias": "Seth Magaziner",
          "code": "Points:  55",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Rhode Island"
        },
        {
          "callsign": "Seth Moulton",
          "alias": "Seth Moulton",
          "code": "Points:  57",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Massachusetts"
        },
        {
          "callsign": "Sharice Davids",
          "alias": "Sharice Davids",
          "code": "Points:  23",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Kansas"
        },
        {
          "callsign": "Sheila Cherfilus-McCormick",
          "alias": "Sheila Cherfilus-McCormick",
          "code": "Points:  59",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Florida"
        },
        {
          "callsign": "Sheila Jackson Lee",
          "alias": "Sheila Jackson Lee",
          "code": "Points:  39",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Texas"
        },
        {
          "callsign": "Shontel Brown",
          "alias": "Shontel Brown",
          "code": "Points:  6",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Ohio"
        },
        {
          "callsign": "Shri Thanedar",
          "alias": "Shri Thanedar",
          "code": "Points:  13",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Michigan"
        },
        {
          "callsign": "Stacey Plaskett",
          "alias": "Stacey Plaskett",
          "code": "Points:  18",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Virgin Islands"
        },
        {
          "callsign": "Steny Hoyer",
          "alias": "Steny Hoyer",
          "code": "Points:  45",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Maryland"
        },
        {
          "callsign": "Stephanie Bice",
          "alias": "Stephanie Bice",
          "code": "Points:  45",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Oklahoma"
        },
        {
          "callsign": "Stephen Lynch",
          "alias": "Stephen Lynch",
          "code": "Points:  19",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Massachusetts"
        },
        {
          "callsign": "Steve Cohen",
          "alias": "Steve Cohen",
          "code": "Points:  57",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Tennessee"
        },
        {
          "callsign": "Steve Scalise",
          "alias": "Steve Scalise",
          "code": "Points:  0",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Louisiana"
        },
        {
          "callsign": "Steve Womack",
          "alias": "Steve Womack",
          "code": "Points:  54",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Arkansas"
        },
        {
          "callsign": "Steven Horsford",
          "alias": "Steven Horsford",
          "code": "Points:  8",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Nevada"
        },
        {
          "callsign": "Summer Lee",
          "alias": "Summer Lee",
          "code": "Points:  25",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Pennsylvania"
        },
        {
          "callsign": "Susan Wild",
          "alias": "Susan Wild",
          "code": "Points:  2",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Pennsylvania"
        },
        {
          "callsign": "Susie Lee",
          "alias": "Susie Lee",
          "code": "Points:  49",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Nevada"
        },
        {
          "callsign": "Suzan DelBene",
          "alias": "Suzan DelBene",
          "code": "Points:  4",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Washington"
        },
        {
          "callsign": "Suzanne Bonamici",
          "alias": "Suzanne Bonamici",
          "code": "Points:  29",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Oregon"
        },
        {
          "callsign": "Sydney Kamlager",
          "alias": "Sydney Kamlager",
          "code": "Points:  18",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "California"
        },
        {
          "callsign": "Sylvia Garcia",
          "alias": "Sylvia Garcia",
          "code": "Points:  54",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Texas"
        },
        {
          "callsign": "Ted Lieu",
          "alias": "Ted Lieu",
          "code": "Points:  54",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "California"
        },
        {
          "callsign": "Teresa Leger Fernandez",
          "alias": "Teresa Leger Fernandez",
          "code": "Points:  12",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "New Mexico"
        },
        {
          "callsign": "Terri Sewell",
          "alias": "Terri Sewell",
          "code": "Points:  1",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Alabama"
        },
        {
          "callsign": "Thomas Kean Jr.",
          "alias": "Thomas Kean Jr.",
          "code": "Points:  37",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "New Jersey"
        },
        {
          "callsign": "Thomas Massie",
          "alias": "Thomas Massie",
          "code": "Points:  24",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Kentucky"
        },
        {
          "callsign": "Tim Burchett",
          "alias": "Tim Burchett",
          "code": "Points:  18",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Tennessee"
        },
        {
          "callsign": "Tim Walberg",
          "alias": "Tim Walberg",
          "code": "Points:  30",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Michigan"
        },
        {
          "callsign": "Tom Cole",
          "alias": "Tom Cole",
          "code": "Points:  45",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Oklahoma"
        },
        {
          "callsign": "Tom Emmer",
          "alias": "Tom Emmer",
          "code": "Points:  6",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Minnesota"
        },
        {
          "callsign": "Tom McClintock",
          "alias": "Tom McClintock",
          "code": "Points:  5",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "California"
        },
        {
          "callsign": "Tom Tiffany",
          "alias": "Tom Tiffany",
          "code": "Points:  56",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Wisconsin"
        },
        {
          "callsign": "Tony Cárdenas",
          "alias": "Tony Cárdenas",
          "code": "Points:  33",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "California"
        },
        {
          "callsign": "Tony Gonzales",
          "alias": "Tony Gonzales",
          "code": "Points:  48",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Texas"
        },
        {
          "callsign": "Tracey Mann",
          "alias": "Tracey Mann",
          "code": "Points:  11",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Kansas"
        },
        {
          "callsign": "Trent Kelly",
          "alias": "Trent Kelly",
          "code": "Points:  7",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Mississippi"
        },
        {
          "callsign": "Troy Balderson",
          "alias": "Troy Balderson",
          "code": "Points:  33",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Ohio"
        },
        {
          "callsign": "Troy Carter",
          "alias": "Troy Carter",
          "code": "Points:  33",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Louisiana"
        },
        {
          "callsign": "Troy Nehls",
          "alias": "Troy Nehls",
          "code": "Points:  38",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Texas"
        },
        {
          "callsign": "Val Hoyle",
          "alias": "Val Hoyle",
          "code": "Points:  46",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Oregon"
        },
        {
          "callsign": "Valerie Foushee",
          "alias": "Valerie Foushee",
          "code": "Points:  39",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "North Carolina"
        },
        {
          "callsign": "Vern Buchanan",
          "alias": "Vern Buchanan",
          "code": "Points:  57",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Florida"
        },
        {
          "callsign": "Veronica Escobar",
          "alias": "Veronica Escobar",
          "code": "Points:  57",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Texas"
        },
        {
          "callsign": "Vicente Gonzalez Jr.",
          "alias": "Vicente Gonzalez Jr.",
          "code": "Points:  25",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Texas"
        },
        {
          "callsign": "Victoria Spartz",
          "alias": "Victoria Spartz",
          "code": "Points:  53",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Indiana"
        },
        {
          "callsign": "Virginia Foxx",
          "alias": "Virginia Foxx",
          "code": "Points:  29",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "North Carolina"
        },
        {
          "callsign": "Warren Davidson",
          "alias": "Warren Davidson",
          "code": "Points:  38",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Ohio"
        },
        {
          "callsign": "Wesley Hunt",
          "alias": "Wesley Hunt",
          "code": "Points:  45",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Texas"
        },
        {
          "callsign": "Wiley Nickel",
          "alias": "Wiley Nickel",
          "code": "Points:  25",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "North Carolina"
        },
        {
          "callsign": "William Timmons",
          "alias": "William Timmons",
          "code": "Points:  51",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "South Carolina"
        },
        {
          "callsign": "Yadira Caraveo",
          "alias": "Yadira Caraveo",
          "code": "Points:  50",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Colorado"
        },
        {
          "callsign": "Young Kim",
          "alias": "Young Kim",
          "code": "Points:  12",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "California"
        },
        {
          "callsign": "Yvette D. Clarke",
          "alias": "Yvette D. Clarke",
          "code": "Points:  29",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "New York"
        },
        {
          "callsign": "Zach Nunn",
          "alias": "Zach Nunn",
          "code": "Points:  59",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Iowa"
        },
        {
          "callsign": "Zoe Lofgren",
          "alias": "Zoe Lofgren",
          "code": "Points:  53",
          "corpro": "Available",
          "frame": "Democratic",
          "mech": "California"
        },
        

 


        {
          "callsign": "Compadre",
          "alias": 'Clint "CC" Cruz',
          "code": "d1fdf62e-d81e-4e10-97c8-df3bc4860117///NDL-C-DEEP-STATION//5a4254aa-9fa2-42ca-a077-8f5bfd1e1ad3",
          "corpro": "GMS",
          "frame": "Everest",
          "mech": "Rio Bravo"
        },
      ],
      "header": {
        "planet": "Hercynia",
        "year": "5014u",
        "system": "Ardennes-3",
        "gate": "Atlas-Quanokrim",
        "ring": "Atlas-Line",
        "headerTitle": "Mirrorsmoke",
        "headerSubtitle": "Mercenary Company",
        "subheaderTitle": "Crisis Response",
        "subheaderSubtitle": "Delta-Echo-Echo-Zulu",
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
  width: 2560px;
  height: 1440px;
  overflow: hidden;
}
</style>