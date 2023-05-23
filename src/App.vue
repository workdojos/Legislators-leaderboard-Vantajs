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
          "callsign": "Aaron",
          "alias": "Aaron Bean",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Florida"
        },
{
          "callsign": "Abigail",
          "alias": "Abigail Spanberger",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Virginia"
        },

{
          "callsign": "Aaron Bean",
          "alias": "Aaron Bean,

          "code": "Points:  8,
          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Florida"
        },
{
          "callsign": "Abigail Spanberger",
          "alias": "Abigail Spanberger,

          "code": "Points:  56,

          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Virginia"
        },
{
          "callsign": "Adam Schiff",
          "alias": "Adam Schiff,

          "code": "Points:  27,

          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "California"
        },
{
          "callsign": "Adrian Smith",
          "alias": "Adrian Smith,

          "code": "Points:  94,

          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Nebraska"
        },
{
          "callsign": "Adriano Espaillat",
          "alias": "Adriano Espaillat,

          "code": "Points:  49,

          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "New York"
        },
{
          "callsign": "Al Green",
          "alias": "Al Green,

          "code": "Points:  41,

          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Texas"
        },
{
          "callsign": "Alexander Mooney",
          "alias": "Alexander Mooney,

          "code": "Points:  73,

          "corpro": "Available",
          "frame": "Republican ",
          "mech": "West Virginia"
        },
{
          "callsign": "Alexandria Ocasio-Cortez",
          "alias": "Alexandria Ocasio-Cortez,

          "code": "Points:  43,

          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "New York"
        },
{
          "callsign": "Alma Adams",
          "alias": "Alma Adams,

          "code": "Points:  67,

          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "North Carolina"
        },
{
          "callsign": "Ami Bera",
          "alias": "Ami Bera,

          "code": "Points:  16,

          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "California"
        },
{
          "callsign": "André Carson",
          "alias": "André Carson,

          "code": "Points:  6,

          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Indiana"
        },
{
          "callsign": "Andrea Salinas",
          "alias": "Andrea Salinas,

          "code": "Points:  88,

          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Oregon"
        },
{
          "callsign": "Andrew Clyde",
          "alias": "Andrew Clyde,

          "code": "Points:  32,

          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Georgia"
        },
{
          "callsign": "Andrew Garbarino",
          "alias": "Andrew Garbarino,

          "code": "Points:  67,

          "corpro": "Available",
          "frame": "Republican ",
          "mech": "New York"
        },
{
          "callsign": "Andrew Harris",
          "alias": "Andrew Harris,

          "code": "Points:  66,

          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Maryland"
        },
{
          "callsign": "Andrew Kim",
          "alias": "Andrew Kim,

          "code": "Points:  7,

          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "New Jersey"
        },
{
          "callsign": "Andy Barr",
          "alias": "Andy Barr,

          "code": "Points:  9,

          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Kentucky"
        },
{
          "callsign": "Andy Biggs",
          "alias": "Andy Biggs,

          "code": "Points:  7,

          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Arizona"
        },
{
          "callsign": "Andy Ogles",
          "alias": "Andy Ogles,

          "code": "Points:  18,

          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Tennessee"
        },
{
          "callsign": "Angie Craig",
          "alias": "Angie Craig,

          "code": "Points:  68,

          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Minnesota"
        },
{
          "callsign": "Ann Wagner",
          "alias": "Ann Wagner,

          "code": "Points:  83,

          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Missouri"
        },
{
          "callsign": "Anna Eshoo",
          "alias": "Anna Eshoo,

          "code": "Points:  83,

          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "California"
        },
{
          "callsign": "Anna Paulina Luna",
          "alias": "Anna Paulina Luna,

          "code": "Points:  1,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Florida"
        },
{
          "callsign": "Annie Kuster",
          "alias": "Annie Kuster,

          "code": "Points:  81,

          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "New Hampshire"
        },
{
          "callsign": "Anthony D'Esposito",
          "alias": "Anthony D'Esposito,

          "code": "Points:  66,

          "corpro": "Available",
          "frame": "Republican ",
          "mech": "New York"
        },
{
          "callsign": "Ashley Hinson",
          "alias": "Ashley Hinson,

          "code": "Points:  44,

          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Iowa"
        },
{
          "callsign": "August Pfluger",
          "alias": "August Pfluger,

          "code": "Points:  53,

          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Texas"
        },
{
          "callsign": "Aumua Amata Radewagen",
          "alias": "Aumua Amata Radewagen,

          "code": "Points:  12,

          "corpro": "Available",
          "frame": "Republican ",
          "mech": "American Samoa"
        },
{
          "callsign": "Austin Scott",
          "alias": "Austin Scott,

          "code": "Points:  60,

          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Georgia"
        },
{
          "callsign": "Ayanna Pressley",
          "alias": "Ayanna Pressley,

          "code": "Points:  76,

          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Massachusetts"
        },
{
          "callsign": "Barbara Lee",
          "alias": "Barbara Lee,

          "code": "Points:  89,

          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "California"
        },
{
          "callsign": "Barry Loudermilk",
          "alias": "Barry Loudermilk,

          "code": "Points:  60,

          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Georgia"
        },
{
          "callsign": "Barry Moore",
          "alias": "Barry Moore,

          "code": "Points:  95,

          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Alabama"
        },
{
          "callsign": "Becca Balint",
          "alias": "Becca Balint,

          "code": "Points:  61,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Vermont"
        },
{
          "callsign": "Benjamin Lee Cline",
          "alias": "Benjamin Lee Cline,

          "code": "Points:  28,

          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Virginia"
        },
{
          "callsign": "Bennie Thompson",
          "alias": "Bennie Thompson,

          "code": "Points:  79,

          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Mississippi"
        },
{
          "callsign": "Beth Van Duyne",
          "alias": "Beth Van Duyne,

          "code": "Points:  76,

          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Texas"
        },
{
          "callsign": "Betty McCollum",
          "alias": "Betty McCollum,

          "code": "Points:  78,

          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Minnesota"
        },
{
          "callsign": "Bill Foster",
          "alias": "Bill Foster,

          "code": "Points:  14,

          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Illinois"
        },
{
          "callsign": "Bill Huizenga",
          "alias": "Bill Huizenga,

          "code": "Points:  70,

          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Michigan"
        },
{
          "callsign": "Bill Johnson",
          "alias": "Bill Johnson,

          "code": "Points:  82,

          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Ohio"
        },
{
          "callsign": "Bill Keating",
          "alias": "Bill Keating,

          "code": "Points:  89,

          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Massachusetts"
        },
{
          "callsign": "Bill Pascrell",
          "alias": "Bill Pascrell,

          "code": "Points:  85,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "New Jersey"
        },
{
          "callsign": "Bill Posey",
          "alias": "Bill Posey,

          "code": "Points:  64,

          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Florida"
        },
{
          "callsign": "Blaine Luetkemeyer",
          "alias": "Blaine Luetkemeyer,

          "code": "Points:  41,

          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Missouri"
        },
{
          "callsign": "Blake Moore",
          "alias": "Blake Moore,

          "code": "Points:  13,

          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Utah"
        },
{
          "callsign": "Bob Good",
          "alias": "Bob Good,

          "code": "Points:  99,

          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Virginia"
        },
{
          "callsign": "Bob Latta",
          "alias": "Bob Latta,

          "code": "Points:  3,

          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Ohio"
        },
{
          "callsign": "Bonnie Watson Coleman",
          "alias": "Bonnie Watson Coleman,

          "code": "Points:  92,

          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "New Jersey"
        },
{
          "callsign": "Brad Finstad",
          "alias": "Brad Finstad,

          "code": "Points:  4,

          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Minnesota"
        },
{
          "callsign": "Brad Schneider",
          "alias": "Brad Schneider,

          "code": "Points:  68,

          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Illinois"
        },
{
          "callsign": "Brad Sherman",
          "alias": "Brad Sherman,

          "code": "Points:  63,

          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "California"
        },
{
          "callsign": "Brad Wenstrup",
          "alias": "Brad Wenstrup,

          "code": "Points:  24,

          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Ohio"
        },
{
          "callsign": "Brandon Williams",
          "alias": "Brandon Williams,

          "code": "Points:  32,

          "corpro": "",
          "frame": "Republican ",
          "mech": "New York"
        },
{
          "callsign": "Brendan Boyle",
          "alias": "Brendan Boyle,

          "code": "Points:  4,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Pennsylvania"
        },
{
          "callsign": "Brett Guthrie",
          "alias": "Brett Guthrie,

          "code": "Points:  97,

          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Kentucky"
        },
{
          "callsign": "Brian Babin",
          "alias": "Brian Babin,

          "code": "Points:  79,

          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Texas"
        },
{
          "callsign": "Brian Fitzpatrick",
          "alias": "Brian Fitzpatrick,

          "code": "Points:  33,

          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Pennsylvania"
        },
{
          "callsign": "Brian Higgins",
          "alias": "Brian Higgins,

          "code": "Points:  0,

          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "New York"
        },
{
          "callsign": "Brian Mast",
          "alias": "Brian Mast,

          "code": "Points:  83,

          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Florida"
        },
{
          "callsign": "Brittany Pettersen",
          "alias": "Brittany Pettersen,

          "code": "Points:  73,

          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Colorado"
        },
{
          "callsign": "Bruce Westerman",
          "alias": "Bruce Westerman,

          "code": "Points:  43,

          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Arkansas"
        },
{
          "callsign": "Bryan Steil",
          "alias": "Bryan Steil,

          "code": "Points:  57,

          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Wisconsin"
        },
{
          "callsign": "Burgess Owens",
          "alias": "Burgess Owens,

          "code": "Points:  79,

          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Utah"
        },
{
          "callsign": "Byron Donalds",
          "alias": "Byron Donalds,

          "code": "Points:  57,

          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Florida"
        },
{
          "callsign": "Carlos Gimenez",
          "alias": "Carlos Gimenez,

          "code": "Points:  78,

          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Florida"
        },
{
          "callsign": "Carol Miller",
          "alias": "Carol Miller,

          "code": "Points:  96,

          "corpro": "Available",
          "frame": "Republican ",
          "mech": "West Virginia"
        },
{
          "callsign": "Cathy McMorris Rodgers",
          "alias": "Cathy McMorris Rodgers,

          "code": "Points:  82,

          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Washington"
        },
{
          "callsign": "Charles J. Fleischmann",
          "alias": "Charles J. Fleischmann,

          "code": "Points:  27,

          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Tennessee"
        },
{
          "callsign": "Chellie Pingree",
          "alias": "Chellie Pingree,

          "code": "Points:  6,

          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Maine"
        },
{
          "callsign": "Chip Roy",
          "alias": "Chip Roy,

          "code": "Points:  41,

          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Texas"
        },
{
          "callsign": "Chris Pappas",
          "alias": "Chris Pappas,

          "code": "Points:  10,

          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "New Hampshire"
        },
{
          "callsign": "Chris Smith",
          "alias": "Chris Smith,

          "code": "Points:  13,

          "corpro": "Available",
          "frame": "Republican ",
          "mech": "New Jersey"
        },
{
          "callsign": "Chris Stewart",
          "alias": "Chris Stewart,

          "code": "Points:  90,

          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Utah"
        },
{
          "callsign": "Chrissy Houlahan",
          "alias": "Chrissy Houlahan,

          "code": "Points:  58,

          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Pennsylvania"
        },
{
          "callsign": "Christopher Deluzio",
          "alias": "Christopher Deluzio,

          "code": "Points:  30,

          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Pennsylvania"
        },
{
          "callsign": "Chuck Edwards",
          "alias": "Chuck Edwards,

          "code": "Points:  11,

          "corpro": "Available",
          "frame": "Republican ",
          "mech": "North Carolina"
        },
{
          "callsign": "Claudia Tenney",
          "alias": "Claudia Tenney,

          "code": "Points:  43,

          "corpro": "Available",
          "frame": "Republican ",
          "mech": "New York"
        },
{
          "callsign": "Clay Higgins",
          "alias": "Clay Higgins,

          "code": "Points:  87,

          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Louisiana"
        },
{
          "callsign": "Cliff Bentz",
          "alias": "Cliff Bentz,

          "code": "Points:  59,

          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Oregon"
        },
{
          "callsign": "Colin Allred",
          "alias": "Colin Allred,

          "code": "Points:  44,

          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Texas"
        },
{
          "callsign": "Cori Bush",
          "alias": "Cori Bush,

          "code": "Points:  50,

          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Missouri"
        },
{
          "callsign": "Cory Mills",
          "alias": "Cory Mills,

          "code": "Points:  88,

          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Florida"
        },
{
          "callsign": "D. Adam Smith",
          "alias": "D. Adam Smith,

          "code": "Points:  21,

          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Washington"
        },
{
          "callsign": "Dale Strong",
          "alias": "Dale Strong,

          "code": "Points:  56,

          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Alabama"
        },
{
          "callsign": "Dan Bishop",
          "alias": "Dan Bishop,

          "code": "Points:  39,

          "corpro": "Available",
          "frame": "Republican ",
          "mech": "North Carolina"
        },
{
          "callsign": "Dan Kildee",
          "alias": "Dan Kildee,

          "code": "Points:  32,

          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Michigan"
        },
{
          "callsign": "Dan Meuser",
          "alias": "Dan Meuser,

          "code": "Points:  30,

          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Pennsylvania"
        },
{
          "callsign": "Dan Newhouse",
          "alias": "Dan Newhouse,

          "code": "Points:  14,

          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Washington"
        },
{
          "callsign": "Daniel Crenshaw",
          "alias": "Daniel Crenshaw,

          "code": "Points:  85,

          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Texas"
        },
{
          "callsign": "Daniel Goldman",
          "alias": "Daniel Goldman,

          "code": "Points:  36,

          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "New York"
        },
{
          "callsign": "Daniel Webster",
          "alias": "Daniel Webster,

          "code": "Points:  58,

          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Florida"
        },
{
          "callsign": "Danny K. Davis",
          "alias": "Danny K. Davis,

          "code": "Points:  60,

          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Illinois"
        },
{
          "callsign": "Darin LaHood",
          "alias": "Darin LaHood,

          "code": "Points:  31,

          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Illinois"
        },
{
          "callsign": "Darrell Issa",
          "alias": "Darrell Issa,

          "code": "Points:  44,

          "corpro": "Available",
          "frame": "Republican ",
          "mech": "California"
        },
{
          "callsign": "Darren Soto",
          "alias": "Darren Soto,

          "code": "Points:  65,

          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Florida"
        },
{
          "callsign": "David G. Valadao",
          "alias": "David G. Valadao,

          "code": "Points:  40,

          "corpro": "Available",
          "frame": "Republican ",
          "mech": "California"
        },
{
          "callsign": "David Joyce",
          "alias": "David Joyce,

          "code": "Points:  77,

          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Ohio"
        },
{
          "callsign": "David Kustoff",
          "alias": "David Kustoff,

          "code": "Points:  63,

          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Tennessee"
        },
{
          "callsign": "David N. Cicilline",
          "alias": "David N. Cicilline,

          "code": "Points:  72,

          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Rhode Island"
        },
{
          "callsign": "David Rouzer",
          "alias": "David Rouzer,

          "code": "Points:  25,

          "corpro": "Available",
          "frame": "Republican ",
          "mech": "North Carolina"
        },
{
          "callsign": "David Schweikert",
          "alias": "David Schweikert,

          "code": "Points:  67,

          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Arizona"
        },
{
          "callsign": "David Scott",
          "alias": "David Scott,

          "code": "Points:  11,

          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Georgia"
        },
{
          "callsign": "David Trone",
          "alias": "David Trone,

          "code": "Points:  56,

          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Maryland"
        },
{
          "callsign": "Dean Phillips",
          "alias": "Dean Phillips,

          "code": "Points:  25,

          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Minnesota"
        },
{
          "callsign": "Debbie Dingell",
          "alias": "Debbie Dingell,

          "code": "Points:  21,

          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Michigan"
        },
{
          "callsign": "Debbie Lesko",
          "alias": "Debbie Lesko,

          "code": "Points:  21,

          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Arizona"
        },
{
          "callsign": "Debbie Wasserman Schultz",
          "alias": "Debbie Wasserman Schultz,

          "code": "Points:  61,

          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Florida"
        },
{
          "callsign": "Deborah Ross",
          "alias": "Deborah Ross,

          "code": "Points:  1,

          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "North Carolina"
        },
{
          "callsign": "Delia Ramirez",
          "alias": "Delia Ramirez,

          "code": "Points:  12,

          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Illinois"
        },
{
          "callsign": "Derek Kilmer",
          "alias": "Derek Kilmer,

          "code": "Points:  15,

          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Washington"
        },
{
          "callsign": "Derrick Van Orden",
          "alias": "Derrick Van Orden,

          "code": "Points:  50,

          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Wisconsin"
        },
{
          "callsign": "Diana DeGette",
          "alias": "Diana DeGette,

          "code": "Points:  49,

          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Colorado"
        },
{
          "callsign": "Diana Harshbarger",
          "alias": "Diana Harshbarger,

          "code": "Points:  54,

          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Tennessee"
        },
{
          "callsign": "Dina Titus",
          "alias": "Dina Titus,

          "code": "Points:  52,

          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Nevada"
        },
{
          "callsign": "Don Bacon",
          "alias": "Don Bacon,

          "code": "Points:  57,

          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Nebraska"
        },
{
          "callsign": "Donald Davis",
          "alias": "Donald Davis,

          "code": "Points:  11,

          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "North Carolina"
        },
{
          "callsign": "Donald Norcross",
          "alias": "Donald Norcross,

          "code": "Points:  31,

          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "New Jersey"
        },
{
          "callsign": "Donald Payne Jr.",
          "alias": "Donald Payne Jr.,

          "code": "Points:  61,

          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "New Jersey"
        },
{
          "callsign": "Donald Sternoff Beyer Jr.",
          "alias": "Donald Sternoff Beyer Jr.,

          "code": "Points:  23,

          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Virginia"
        },
{
          "callsign": "Doris Matsui",
          "alias": "Doris Matsui,

          "code": "Points:  48,

          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "California"
        },
{
          "callsign": "Doug LaMalfa",
          "alias": "Doug LaMalfa,

          "code": "Points:  33,

          "corpro": "Available",
          "frame": "Republican ",
          "mech": "California"
        },
{
          "callsign": "Doug Lamborn",
          "alias": "Doug Lamborn,

          "code": "Points:  60,

          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Colorado"
        },
{
          "callsign": "Drew Ferguson",
          "alias": "Drew Ferguson,

          "code": "Points:  13,

          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Georgia"
        },
{
          "callsign": "Dusty Johnson",
          "alias": "Dusty Johnson,

          "code": "Points:  50,

          "corpro": "Available",
          "frame": "Republican ",
          "mech": "South Dakota"
        },
{
          "callsign": "Dutch Ruppersberger",
          "alias": "Dutch Ruppersberger,

          "code": "Points:  37,

          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Maryland"
        },
{
          "callsign": "Dwight Evans",
          "alias": "Dwight Evans,

          "code": "Points:  53,

          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Pennsylvania"
        },
{
          "callsign": "Earl Blumenauer",
          "alias": "Earl Blumenauer,

          "code": "Points:  47,

          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Oregon"
        },
{
          "callsign": "Earl Carter",
          "alias": "Earl Carter,

          "code": "Points:  87,

          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Georgia"
        },
{
          "callsign": "Ed Case",
          "alias": "Ed Case,

          "code": "Points:  72,

          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Hawaii"
        },
{
          "callsign": "Eleanor Holmes Norton",
          "alias": "Eleanor Holmes Norton,

          "code": "Points:  73,

          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Non-Voting"
        },
{
          "callsign": "Eli Crane",
          "alias": "Eli Crane,

          "code": "Points:  45,

          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Arizona"
        },
{
          "callsign": "Elise Stefanik",
          "alias": "Elise Stefanik,

          "code": "Points:  74,

          "corpro": "Available",
          "frame": "Republican ",
          "mech": "New York"
        },
{
          "callsign": "Elissa Slotkin",
          "alias": "Elissa Slotkin,

          "code": "Points:  35,

          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Michigan"
        },
{
          "callsign": "Emanuel Cleaver",
          "alias": "Emanuel Cleaver,

          "code": "Points:  32,

          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Missouri"
        },
{
          "callsign": "Emilia Sykes",
          "alias": "Emilia Sykes,

          "code": "Points:  37,

          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Ohio"
        },
{
          "callsign": "Eric Burlison",
          "alias": "Eric Burlison,

          "code": "Points:  54,

          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Missouri"
        },
{
          "callsign": "Eric Sorensen",
          "alias": "Eric Sorensen,

          "code": "Points:  72,

          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Illinois"
        },
{
          "callsign": "Eric Swalwell",
          "alias": "Eric Swalwell,

          "code": "Points:  68,

          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "California"
        },
{
          "callsign": "Erin Houchin",
          "alias": "Erin Houchin,

          "code": "Points:  19,

          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Indiana"
        },
{
          "callsign": "Frank Lucas",
          "alias": "Frank Lucas,

          "code": "Points:  86,

          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Oklahoma"
        },
{
          "callsign": "Frank Mrvan",
          "alias": "Frank Mrvan,

          "code": "Points:  0,

          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Indiana"
        },
{
          "callsign": "Frank Pallone Jr.",
          "alias": "Frank Pallone Jr.,

          "code": "Points:  69,

          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "New Jersey"
        },
{
          "callsign": "Frederica S. Wilson",
          "alias": "Frederica S. Wilson,

          "code": "Points:  35,

          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Florida"
        },
{
          "callsign": "French Hill",
          "alias": "French Hill,

          "code": "Points:  17,

          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Arkansas"
        },
{
          "callsign": "Gabriel Vasquez",
          "alias": "Gabriel Vasquez,

          "code": "Points:  37,

          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "New Mexico"
        },
{
          "callsign": "Garret Graves",
          "alias": "Garret Graves,

          "code": "Points:  21,

          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Louisiana"
        },
{
          "callsign": "Gary Palmer",
          "alias": "Gary Palmer,

          "code": "Points:  53,

          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Alabama"
        },
{
          "callsign": "George Devolder-Santos",
          "alias": "George Devolder-Santos,

          "code": "Points:  70,

          "corpro": "",
          "frame": "Republican ",
          "mech": "New York"
        },
{
          "callsign": "Gerald Edward Connolly",
          "alias": "Gerald Edward Connolly,

          "code": "Points:  56,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Virginia"
        },
{
          "callsign": "Glenn Grothman",
          "alias": "Glenn Grothman,

          "code": "Points:  29,

          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Wisconsin"
        },
{
          "callsign": "Glenn Ivey",
          "alias": "Glenn Ivey,

          "code": "Points:  39,

          "corpro": "Available",
          "frame": "Democratic ",
          "mech": "Maryland"
        },
{
          "callsign": "Glenn Thompson",
          "alias": "Glenn Thompson,

          "code": "Points:  74,

          "corpro": "Available",
          "frame": "Republican ",
          "mech": "Pennsylvania"
        },
 
{
          "callsign": "Grace Napolitano",
          "alias": "Grace Napolitano,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "California"
        },
{
          "callsign": "Greg Casar",
          "alias": "Greg Casar,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Texas"
        },
{
          "callsign": "Greg Landsman",
          "alias": "Greg Landsman,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Ohio"
        },
{
          "callsign": "Greg Pence",
          "alias": "Greg Pence,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Indiana"
        },
{
          "callsign": "Greg Stanton",
          "alias": "Greg Stanton,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Arizona"
        },
{
          "callsign": "Greg Steube",
          "alias": "Greg Steube,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Florida"
        },
{
          "callsign": "Gregorio Kilili Camacho Sablan",
          "alias": "Gregorio Kilili Camacho Sablan,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Northern Mariana Islands"
        },
{
          "callsign": "Gregory Murphy",
          "alias": "Gregory Murphy,

          "corpro": "",
          "frame": "Republican ",
          "mech": "North Carolina"
        },
{
          "callsign": "Gregory W. Meeks",
          "alias": "Gregory W. Meeks,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "New York"
        },
{
          "callsign": "Gus M. Bilirakis",
          "alias": "Gus M. Bilirakis,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Florida"
        },
{
          "callsign": "Guy Reschenthaler",
          "alias": "Guy Reschenthaler,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Pennsylvania"
        },
{
          "callsign": "Gwen Moore",
          "alias": "Gwen Moore,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Wisconsin"
        },
{
          "callsign": "H. Morgan Griffith",
          "alias": "H. Morgan Griffith,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Virginia"
        },
{
          "callsign": "Hakeem Jeffries",
          "alias": "Hakeem Jeffries,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "New York"
        },
{
          "callsign": "Hal Rogers",
          "alias": "Hal Rogers,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Kentucky"
        },
{
          "callsign": "Haley Stevens",
          "alias": "Haley Stevens,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Michigan"
        },
{
          "callsign": "Hank Johnson",
          "alias": "Hank Johnson,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Georgia"
        },
{
          "callsign": "Harriet Hageman",
          "alias": "Harriet Hageman,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Wyoming"
        },
{
          "callsign": "Henry Cuellar",
          "alias": "Henry Cuellar,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Texas"
        },
{
          "callsign": "Hillary Scholten",
          "alias": "Hillary Scholten,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Michigan"
        },
{
          "callsign": "Ilhan Omar",
          "alias": "Ilhan Omar,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Minnesota"
        },
{
          "callsign": "Jack Bergman",
          "alias": "Jack Bergman,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Michigan"
        },
{
          "callsign": "Jacob LaTurner",
          "alias": "Jacob LaTurner,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Kansas"
        },
{
          "callsign": "Jahana Hayes",
          "alias": "Jahana Hayes,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Connecticut"
        },
{
          "callsign": "Jake Auchincloss",
          "alias": "Jake Auchincloss,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Massachusetts"
        },
{
          "callsign": "Jake Ellzey",
          "alias": "Jake Ellzey,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Texas"
        },
{
          "callsign": "Jamaal Bowman",
          "alias": "Jamaal Bowman,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "New York"
        },
{
          "callsign": "James Clyburn",
          "alias": "James Clyburn,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "South Carolina"
        },
{
          "callsign": "James Comer Jr.",
          "alias": "James Comer Jr.,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Kentucky"
        },
{
          "callsign": "James Moylan",
          "alias": "James Moylan,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Guam"
        },
{
          "callsign": "Jamie Raskin",
          "alias": "Jamie Raskin,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Maryland"
        },
{
          "callsign": "Jan Schakowsky",
          "alias": "Jan Schakowsky,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Illinois"
        },
{
          "callsign": "Jared Evan Moskowitz",
          "alias": "Jared Evan Moskowitz,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Florida"
        },
{
          "callsign": "Jared Golden",
          "alias": "Jared Golden,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Maine"
        },
{
          "callsign": "Jared Huffman",
          "alias": "Jared Huffman,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "California"
        },
{
          "callsign": "Jasmine Crockett",
          "alias": "Jasmine Crockett,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Texas"
        },
{
          "callsign": "Jason Crow",
          "alias": "Jason Crow,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Colorado"
        },
{
          "callsign": "Jason Smith",
          "alias": "Jason Smith,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Missouri"
        },
{
          "callsign": "Jay Obernolte",
          "alias": "Jay Obernolte,

          "corpro": "",
          "frame": "Republican ",
          "mech": "California"
        },
{
          "callsign": "Jeff Duncan",
          "alias": "Jeff Duncan,

          "corpro": "",
          "frame": "Republican ",
          "mech": "South Carolina"
        },
{
          "callsign": "Jeff Jackson",
          "alias": "Jeff Jackson,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "North Carolina"
        },
{
          "callsign": "Jeff Van Drew",
          "alias": "Jeff Van Drew,

          "corpro": "",
          "frame": "Republican ",
          "mech": "New Jersey"
        },
{
          "callsign": "Jennifer Kiggans",
          "alias": "Jennifer Kiggans,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Virginia"
        },
{
          "callsign": "Jennifer McClellan",
          "alias": "Jennifer McClellan,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Virginia"
        },
{
          "callsign": "Jennifer Wexton",
          "alias": "Jennifer Wexton,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Virginia"
        },
{
          "callsign": "Jerrold Nadler",
          "alias": "Jerrold Nadler,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "New York"
        },
{
          "callsign": "Jerry Carl",
          "alias": "Jerry Carl,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Alabama"
        },
{
          "callsign": "Jesus Garcia",
          "alias": "Jesus Garcia,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Illinois"
        },
{
          "callsign": "Jill Tokuda",
          "alias": "Jill Tokuda,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Hawaii"
        },
{
          "callsign": "Jim Baird",
          "alias": "Jim Baird,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Indiana"
        },
{
          "callsign": "Jim Banks",
          "alias": "Jim Banks,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Indiana"
        },
{
          "callsign": "Jim Costa",
          "alias": "Jim Costa,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "California"
        },
{
          "callsign": "Jim Himes",
          "alias": "Jim Himes,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Connecticut"
        },
{
          "callsign": "Jim Jordan",
          "alias": "Jim Jordan,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Ohio"
        },
{
          "callsign": "Jim McGovern",
          "alias": "Jim McGovern,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Massachusetts"
        },
{
          "callsign": "Jimmy Gomez",
          "alias": "Jimmy Gomez,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "California"
        },
{
          "callsign": "Jimmy Panetta",
          "alias": "Jimmy Panetta,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "California"
        },
{
          "callsign": "Joaquin Castro",
          "alias": "Joaquin Castro,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Texas"
        },
{
          "callsign": "Jodey Arrington",
          "alias": "Jodey Arrington,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Texas"
        },
{
          "callsign": "Joe Courtney",
          "alias": "Joe Courtney,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Connecticut"
        },
{
          "callsign": "Joe Neguse",
          "alias": "Joe Neguse,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Colorado"
        },
{
          "callsign": "Joe Wilson",
          "alias": "Joe Wilson,

          "corpro": "",
          "frame": "Republican ",
          "mech": "South Carolina"
        },
{
          "callsign": "John Carter",
          "alias": "John Carter,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Texas"
        },
{
          "callsign": "John Curtis",
          "alias": "John Curtis,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Utah"
        },
{
          "callsign": "John Duarte",
          "alias": "John Duarte,

          "corpro": "",
          "frame": "Republican ",
          "mech": "California"
        },
{
          "callsign": "John Garamendi",
          "alias": "John Garamendi,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "California"
        },
{
          "callsign": "John James",
          "alias": "John James,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Michigan"
        },
{
          "callsign": "John Joyce",
          "alias": "John Joyce,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Pennsylvania"
        },
{
          "callsign": "John Larson",
          "alias": "John Larson,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Connecticut"
        },
{
          "callsign": "John Moolenaar",
          "alias": "John Moolenaar,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Michigan"
        },
{
          "callsign": "John Rose",
          "alias": "John Rose,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Tennessee"
        },
{
          "callsign": "John Rutherford",
          "alias": "John Rutherford,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Florida"
        },
{
          "callsign": "John Sarbanes",
          "alias": "John Sarbanes,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Maryland"
        },
{
          "callsign": "Jonathan Jackson",
          "alias": "Jonathan Jackson,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Illinois"
        },
{
          "callsign": "Joseph Morelle",
          "alias": "Joseph Morelle,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "New York"
        },
{
          "callsign": "Josh Brecheen",
          "alias": "Josh Brecheen,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Oklahoma"
        },
{
          "callsign": "Josh Gottheimer",
          "alias": "Josh Gottheimer,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "New Jersey"
        },
{
          "callsign": "Josh Harder",
          "alias": "Josh Harder,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "California"
        },
{
          "callsign": "Joyce Beatty",
          "alias": "Joyce Beatty,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Ohio"
        },
{
          "callsign": "Juan Ciscomani",
          "alias": "Juan Ciscomani,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Arizona"
        },
{
          "callsign": "Juan Vargas",
          "alias": "Juan Vargas,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "California"
        },
{
          "callsign": "Judy Chu",
          "alias": "Judy Chu,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "California"
        },
{
          "callsign": "Julia Brownley",
          "alias": "Julia Brownley,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "California"
        },
{
          "callsign": "Julia Letlow",
          "alias": "Julia Letlow,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Louisiana"
        },
{
          "callsign": "Kat Cammack",
          "alias": "Kat Cammack,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Florida"
        },
{
          "callsign": "Katherine Clark",
          "alias": "Katherine Clark,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Massachusetts"
        },
{
          "callsign": "Kathy Castor",
          "alias": "Kathy Castor,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Florida"
        },
{
          "callsign": "Kathy Manning",
          "alias": "Kathy Manning,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "North Carolina"
        },
{
          "callsign": "Katie Porter",
          "alias": "Katie Porter,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "California"
        },
{
          "callsign": "Kay Granger",
          "alias": "Kay Granger,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Texas"
        },
{
          "callsign": "Keith Self",
          "alias": "Keith Self,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Texas"
        },
{
          "callsign": "Kelly Armstrong",
          "alias": "Kelly Armstrong,

          "corpro": "",
          "frame": "Republican ",
          "mech": "North Dakota"
        },
{
          "callsign": "Ken Buck",
          "alias": "Ken Buck,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Colorado"
        },
{
          "callsign": "Ken Calvert",
          "alias": "Ken Calvert,

          "corpro": "",
          "frame": "Republican ",
          "mech": "California"
        },
{
          "callsign": "Kevin Hern",
          "alias": "Kevin Hern,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Oklahoma"
        },
{
          "callsign": "Kevin Kiley",
          "alias": "Kevin Kiley,

          "corpro": "",
          "frame": "Republican ",
          "mech": "California"
        },
{
          "callsign": "Kevin McCarthy",
          "alias": "Kevin McCarthy,

          "corpro": "",
          "frame": "Republican ",
          "mech": "California"
        },
{
          "callsign": "Kevin Mullin",
          "alias": "Kevin Mullin,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "California"
        },
{
          "callsign": "Kim Schrier",
          "alias": "Kim Schrier,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Washington"
        },
{
          "callsign": "Kweisi Mfume",
          "alias": "Kweisi Mfume,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Maryland"
        },
{
          "callsign": "Lance Gooden",
          "alias": "Lance Gooden,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Texas"
        },
{
          "callsign": "Larry Bucshon",
          "alias": "Larry Bucshon,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Indiana"
        },
{
          "callsign": "Laurel Lee",
          "alias": "Laurel Lee,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Florida"
        },
{
          "callsign": "Lauren Boebert",
          "alias": "Lauren Boebert,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Colorado"
        },
{
          "callsign": "Lauren Underwood",
          "alias": "Lauren Underwood,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Illinois"
        },
{
          "callsign": "Linda Sánchez",
          "alias": "Linda Sánchez,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "California"
        },
{
          "callsign": "Lisa Blunt Rochester",
          "alias": "Lisa Blunt Rochester,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Delaware"
        },
{
          "callsign": "Lisa McClain",
          "alias": "Lisa McClain,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Michigan"
        },
{
          "callsign": "Lizzie Pannill Fletcher",
          "alias": "Lizzie Pannill Fletcher,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Texas"
        },
{
          "callsign": "Lloyd Doggett",
          "alias": "Lloyd Doggett,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Texas"
        },
{
          "callsign": "Lloyd Smucker",
          "alias": "Lloyd Smucker,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Pennsylvania"
        },
{
          "callsign": "Lois Frankel",
          "alias": "Lois Frankel,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Florida"
        },
{
          "callsign": "Lori Chavez-DeRemer",
          "alias": "Lori Chavez-DeRemer,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Oregon"
        },
{
          "callsign": "Lori Trahan",
          "alias": "Lori Trahan,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Massachusetts"
        },
{
          "callsign": "Lou Correa",
          "alias": "Lou Correa,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "California"
        },
{
          "callsign": "Lucy McBath",
          "alias": "Lucy McBath,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Georgia"
        },
{
          "callsign": "Madeleine Dean",
          "alias": "Madeleine Dean,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Pennsylvania"
        },
{
          "callsign": "Marc Veasey",
          "alias": "Marc Veasey,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Texas"
        },
{
          "callsign": "Marcus Molinaro",
          "alias": "Marcus Molinaro,

          "corpro": "",
          "frame": "Republican ",
          "mech": "New York"
        },
{
          "callsign": "Marcy Kaptur",
          "alias": "Marcy Kaptur,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Ohio"
        },
{
          "callsign": "Maria Elvira Salazar",
          "alias": "Maria Elvira Salazar,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Florida"
        },
{
          "callsign": "Mariannette Miller-Meeks",
          "alias": "Mariannette Miller-Meeks,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Iowa"
        },
{
          "callsign": "Marie Gluesenkamp Pérez",
          "alias": "Marie Gluesenkamp Pérez,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Washington"
        },
{
          "callsign": "Marilyn Strickland",
          "alias": "Marilyn Strickland,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Washington"
        },
{
          "callsign": "Mario Diaz-Balart",
          "alias": "Mario Diaz-Balart,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Florida"
        },
{
          "callsign": "Marjorie Taylor Greene",
          "alias": "Marjorie Taylor Greene,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Georgia"
        },
{
          "callsign": "Mark Alford",
          "alias": "Mark Alford,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Missouri"
        },
{
          "callsign": "Mark Amodei",
          "alias": "Mark Amodei,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Nevada"
        },
{
          "callsign": "Mark DeSaulnier",
          "alias": "Mark DeSaulnier,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "California"
        },
{
          "callsign": "Mark Green",
          "alias": "Mark Green,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Tennessee"
        },
{
          "callsign": "Mark Pocan",
          "alias": "Mark Pocan,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Wisconsin"
        },
{
          "callsign": "Mark Takano",
          "alias": "Mark Takano,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "California"
        },
{
          "callsign": "Mary Gay Scanlon",
          "alias": "Mary Gay Scanlon,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Pennsylvania"
        },
{
          "callsign": "Mary Miller",
          "alias": "Mary Miller,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Illinois"
        },
{
          "callsign": "Mary Peltola",
          "alias": "Mary Peltola,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Alaska"
        },
{
          "callsign": "Matt Cartwright",
          "alias": "Matt Cartwright,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Pennsylvania"
        },
{
          "callsign": "Matt Gaetz",
          "alias": "Matt Gaetz,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Florida"
        },
{
          "callsign": "Matt Rosendale",
          "alias": "Matt Rosendale,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Montana"
        },
{
          "callsign": "Max Miller",
          "alias": "Max Miller,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Ohio"
        },
{
          "callsign": "Maxine Waters",
          "alias": "Maxine Waters,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "California"
        },
{
          "callsign": "Maxwell Alejandro Frost",
          "alias": "Maxwell Alejandro Frost,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Florida"
        },
{
          "callsign": "Melanie Ann Stansbury",
          "alias": "Melanie Ann Stansbury,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "New Mexico"
        },
{
          "callsign": "Michael C. Burgess",
          "alias": "Michael C. Burgess,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Texas"
        },
{
          "callsign": "Michael Cloud",
          "alias": "Michael Cloud,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Texas"
        },
{
          "callsign": "Michael Guest",
          "alias": "Michael Guest,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Mississippi"
        },
{
          "callsign": "Michael K. Simpson",
          "alias": "Michael K. Simpson,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Idaho"
        },
{
          "callsign": "Michael Lawler",
          "alias": "Michael Lawler,

          "corpro": "",
          "frame": "Republican ",
          "mech": "New York"
        },
{
          "callsign": "Michael McCaul",
          "alias": "Michael McCaul,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Texas"
        },
{
          "callsign": "Michael Turner",
          "alias": "Michael Turner,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Ohio"
        },
{
          "callsign": "Michael Waltz",
          "alias": "Michael Waltz,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Florida"
        },
{
          "callsign": "Michelle Fischbach",
          "alias": "Michelle Fischbach,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Minnesota"
        },
{
          "callsign": "Michelle Steel",
          "alias": "Michelle Steel,

          "corpro": "",
          "frame": "Republican ",
          "mech": "California"
        },
{
          "callsign": "Mike Bost",
          "alias": "Mike Bost,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Illinois"
        },
{
          "callsign": "Mike Carey",
          "alias": "Mike Carey,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Ohio"
        },
{
          "callsign": "Mike Collins",
          "alias": "Mike Collins,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Georgia"
        },
{
          "callsign": "Mike Ezell",
          "alias": "Mike Ezell,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Mississippi"
        },
{
          "callsign": "Mike Flood",
          "alias": "Mike Flood,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Nebraska"
        },
{
          "callsign": "Mike Gallagher",
          "alias": "Mike Gallagher,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Wisconsin"
        },
{
          "callsign": "Mike Garcia",
          "alias": "Mike Garcia,

          "corpro": "",
          "frame": "Republican ",
          "mech": "California"
        },
{
          "callsign": "Mike Johnson",
          "alias": "Mike Johnson,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Louisiana"
        },
{
          "callsign": "Mike Kelly",
          "alias": "Mike Kelly,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Pennsylvania"
        },
{
          "callsign": "Mike Levin",
          "alias": "Mike Levin,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "California"
        },
{
          "callsign": "Mike Quigley",
          "alias": "Mike Quigley,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Illinois"
        },
{
          "callsign": "Mike Rogers",
          "alias": "Mike Rogers,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Alabama"
        },
{
          "callsign": "Mike Thompson",
          "alias": "Mike Thompson,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "California"
        },
{
          "callsign": "Mikie Sherrill",
          "alias": "Mikie Sherrill,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "New Jersey"
        },
{
          "callsign": "Monica De La Cruz",
          "alias": "Monica De La Cruz,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Texas"
        },
{
          "callsign": "Morgan Luttrell",
          "alias": "Morgan Luttrell,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Texas"
        },
{
          "callsign": "Morgan McGarvey",
          "alias": "Morgan McGarvey,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Kentucky"
        },
{
          "callsign": "Nancy Mace",
          "alias": "Nancy Mace,

          "corpro": "",
          "frame": "Republican ",
          "mech": "South Carolina"
        },
{
          "callsign": "Nancy Pelosi",
          "alias": "Nancy Pelosi,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "California"
        },
{
          "callsign": "Nanette Barragán",
          "alias": "Nanette Barragán,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "California"
        },
{
          "callsign": "Nathaniel Moran",
          "alias": "Nathaniel Moran,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Texas"
        },
{
          "callsign": "Neal Dunn",
          "alias": "Neal Dunn,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Florida"
        },
{
          "callsign": "Nicholas A. Langworthy",
          "alias": "Nicholas A. Langworthy,

          "corpro": "",
          "frame": "Republican ",
          "mech": "New York"
        },
{
          "callsign": "Nicholas J. LaLota",
          "alias": "Nicholas J. LaLota,

          "corpro": "",
          "frame": "Republican ",
          "mech": "New York"
        },
{
          "callsign": "Nicole Malliotakis",
          "alias": "Nicole Malliotakis,

          "corpro": "",
          "frame": "Republican ",
          "mech": "New York"
        },
{
          "callsign": "Nikema Williams",
          "alias": "Nikema Williams,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Georgia"
        },
{
          "callsign": "Nikki Budzinski",
          "alias": "Nikki Budzinski,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Illinois"
        },
{
          "callsign": "Norma Torres",
          "alias": "Norma Torres,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "California"
        },
{
          "callsign": "Nydia Velazquez",
          "alias": "Nydia Velazquez,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "New"
        },
{
          "callsign": "Pat Fallon",
          "alias": "Pat Fallon,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Texas"
        },
{
          "callsign": "Pat Ryan",
          "alias": "Pat Ryan,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "New"
        },
{
          "callsign": "Patrick T. McHenry",
          "alias": "Patrick T. McHenry,

          "corpro": "",
          "frame": "Republican ",
          "mech": "North Carolina"
        },
{
          "callsign": "Paul Gosar",
          "alias": "Paul Gosar,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Arizona"
        },
{
          "callsign": "Paul Tonko",
          "alias": "Paul Tonko,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "New York"
        },
{
          "callsign": "Pete Aguilar",
          "alias": "Pete Aguilar,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "California"
        },
{
          "callsign": "Pete Sessions",
          "alias": "Pete Sessions,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Texas"
        },
{
          "callsign": "Pete Stauber",
          "alias": "Pete Stauber,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Minnesota"
        },
{
          "callsign": "Pramila Jayapal",
          "alias": "Pramila Jayapal,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Washington"
        },
{
          "callsign": "Raja Krishnamoorthi",
          "alias": "Raja Krishnamoorthi,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Illinois"
        },
{
          "callsign": "Ralph Norman",
          "alias": "Ralph Norman,

          "corpro": "",
          "frame": "Republican ",
          "mech": "South Carolina"
        },
{
          "callsign": "Randy Feenstra",
          "alias": "Randy Feenstra,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Iowa"
        },
{
          "callsign": "Randy Weber",
          "alias": "Randy Weber,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Texas"
        },
{
          "callsign": "Rashida Tlaib",
          "alias": "Rashida Tlaib,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Michigan"
        },
{
          "callsign": "Raúl Grijalva",
          "alias": "Raúl Grijalva,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Arizona"
        },
{
          "callsign": "Raul Ruiz",
          "alias": "Raul Ruiz,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "California"
        },
{
          "callsign": "Rich McCormick",
          "alias": "Rich McCormick,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Georgia"
        },
{
          "callsign": "Richard Hudson",
          "alias": "Richard Hudson,

          "corpro": "",
          "frame": "Republican ",
          "mech": "North Carolina"
        },
{
          "callsign": "Richard Neal",
          "alias": "Richard Neal,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Massachusetts"
        },
{
          "callsign": "Rick Allen",
          "alias": "Rick Allen,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Georgia"
        },
{
          "callsign": "Rick Crawford",
          "alias": "Rick Crawford,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Arkansas"
        },
{
          "callsign": "Rick Larsen",
          "alias": "Rick Larsen,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Washington"
        },
{
          "callsign": "Ritchie Torres",
          "alias": "Ritchie Torres,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "New York"
        },
{
          "callsign": "Ro Khanna",
          "alias": "Ro Khanna,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "California"
        },
{
          "callsign": "Robert Aderholt",
          "alias": "Robert Aderholt,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Alabama"
        },
{
          "callsign": "Robert C. Scott",
          "alias": "Robert C. Scott,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Virginia"
        },
{
          "callsign": "Robert Garcia",
          "alias": "Robert Garcia,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "California"
        },
{
          "callsign": "Robert J. Wittman",
          "alias": "Robert J. Wittman,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Virginia"
        },
{
          "callsign": "Robert Menendez Jr.",
          "alias": "Robert Menendez Jr.,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "New Jersey"
        },
{
          "callsign": "Robin Kelly",
          "alias": "Robin Kelly,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Illinois"
        },
{
          "callsign": "Roger Williams",
          "alias": "Roger Williams,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Texas"
        },
{
          "callsign": "Ron Estes",
          "alias": "Ron Estes,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Kansas"
        },
{
          "callsign": "Ronny L. Jackson",
          "alias": "Ronny L. Jackson,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Texas"
        },
{
          "callsign": "Rosa L. DeLauro",
          "alias": "Rosa L. DeLauro,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Connecticut"
        },
{
          "callsign": "Ruben Gallego",
          "alias": "Ruben Gallego,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Arizona"
        },
{
          "callsign": "Rudy Yakym",
          "alias": "Rudy Yakym,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Indiana"
        },
{
          "callsign": "Russ Fulcher",
          "alias": "Russ Fulcher,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Idaho"
        },
{
          "callsign": "Russell Fry",
          "alias": "Russell Fry,

          "corpro": "",
          "frame": "Republican ",
          "mech": "South Carolina"
        },
{
          "callsign": "Ryan Zinke",
          "alias": "Ryan Zinke,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Montana"
        },
{
          "callsign": "Salud Carbajal",
          "alias": "Salud Carbajal,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "California"
        },
{
          "callsign": "Sam Graves",
          "alias": "Sam Graves,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Missouri"
        },
{
          "callsign": "Sanford Bishop Jr.",
          "alias": "Sanford Bishop Jr.,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Georgia"
        },
{
          "callsign": "Sara Jacobs",
          "alias": "Sara Jacobs,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "California"
        },
{
          "callsign": "Scott DesJarlais",
          "alias": "Scott DesJarlais,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Tennessee"
        },
{
          "callsign": "Scott Fitzgerald",
          "alias": "Scott Fitzgerald,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Wisconsin"
        },
{
          "callsign": "Scott Franklin",
          "alias": "Scott Franklin,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Florida"
        },
{
          "callsign": "Scott Perry",
          "alias": "Scott Perry,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Pennsylvania"
        },
{
          "callsign": "Scott Peters",
          "alias": "Scott Peters,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "California"
        },
{
          "callsign": "Sean Casten",
          "alias": "Sean Casten,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Illinois"
        },
{
          "callsign": "Seth Magaziner",
          "alias": "Seth Magaziner,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Rhode Island"
        },
{
          "callsign": "Seth Moulton",
          "alias": "Seth Moulton,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Massachusetts"
        },
{
          "callsign": "Sharice Davids",
          "alias": "Sharice Davids,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Kansas"
        },
{
          "callsign": "Sheila Cherfilus-McCormick",
          "alias": "Sheila Cherfilus-McCormick,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Florida"
        },
{
          "callsign": "Sheila Jackson Lee",
          "alias": "Sheila Jackson Lee,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Texas"
        },
{
          "callsign": "Shontel Brown",
          "alias": "Shontel Brown,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Ohio"
        },
{
          "callsign": "Shri Thanedar",
          "alias": "Shri Thanedar,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Michigan"
        },
{
          "callsign": "Stacey Plaskett",
          "alias": "Stacey Plaskett,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Virgin Islands"
        },
{
          "callsign": "Steny Hoyer",
          "alias": "Steny Hoyer,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Maryland"
        },
{
          "callsign": "Stephanie Bice",
          "alias": "Stephanie Bice,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Oklahoma"
        },
{
          "callsign": "Stephen Lynch",
          "alias": "Stephen Lynch,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Massachusetts"
        },
{
          "callsign": "Steve Cohen",
          "alias": "Steve Cohen,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Tennessee"
        },
{
          "callsign": "Steve Scalise",
          "alias": "Steve Scalise,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Louisiana"
        },
{
          "callsign": "Steve Womack",
          "alias": "Steve Womack,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Arkansas"
        },
{
          "callsign": "Steven Horsford",
          "alias": "Steven Horsford,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Nevada"
        },
{
          "callsign": "Summer Lee",
          "alias": "Summer Lee,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Pennsylvania"
        },
{
          "callsign": "Susan Wild",
          "alias": "Susan Wild,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Pennsylvania"
        },
{
          "callsign": "Susie Lee",
          "alias": "Susie Lee,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Nevada"
        },
{
          "callsign": "Suzan DelBene",
          "alias": "Suzan DelBene,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Washington"
        },
{
          "callsign": "Suzanne Bonamici",
          "alias": "Suzanne Bonamici,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Oregon"
        },
{
          "callsign": "Sydney Kamlager",
          "alias": "Sydney Kamlager,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "California"
        },
{
          "callsign": "Sylvia Garcia",
          "alias": "Sylvia Garcia,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Texas"
        },
{
          "callsign": "Ted Lieu",
          "alias": "Ted Lieu,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "California"
        },
{
          "callsign": "Teresa Leger Fernandez",
          "alias": "Teresa Leger Fernandez,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "New Mexico"
        },
{
          "callsign": "Terri Sewell",
          "alias": "Terri Sewell,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Alabama"
        },
{
          "callsign": "Thomas Kean Jr.",
          "alias": "Thomas Kean Jr.,

          "corpro": "",
          "frame": "Republican ",
          "mech": "New Jersey"
        },
{
          "callsign": "Thomas Massie",
          "alias": "Thomas Massie,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Kentucky"
        },
{
          "callsign": "Tim Burchett",
          "alias": "Tim Burchett,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Tennessee"
        },
{
          "callsign": "Tim Walberg",
          "alias": "Tim Walberg,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Michigan"
        },
{
          "callsign": "Tom Cole",
          "alias": "Tom Cole,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Oklahoma"
        },
{
          "callsign": "Tom Emmer",
          "alias": "Tom Emmer,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Minnesota"
        },
{
          "callsign": "Tom McClintock",
          "alias": "Tom McClintock,

          "corpro": "",
          "frame": "Republican ",
          "mech": "California"
        },
{
          "callsign": "Tom Tiffany",
          "alias": "Tom Tiffany,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Wisconsin"
        },
{
          "callsign": "Tony Cárdenas",
          "alias": "Tony Cárdenas,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "California"
        },
{
          "callsign": "Tony Gonzales",
          "alias": "Tony Gonzales,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Texas"
        },
{
          "callsign": "Tracey Mann",
          "alias": "Tracey Mann,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Kansas"
        },
{
          "callsign": "Trent Kelly",
          "alias": "Trent Kelly,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Mississippi"
        },
{
          "callsign": "Troy Balderson",
          "alias": "Troy Balderson,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Ohio"
        },
{
          "callsign": "Troy Carter",
          "alias": "Troy Carter,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Louisiana"
        },
{
          "callsign": "Troy Nehls",
          "alias": "Troy Nehls,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Texas"
        },
{
          "callsign": "Val Hoyle",
          "alias": "Val Hoyle,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Oregon"
        },
{
          "callsign": "Valerie Foushee",
          "alias": "Valerie Foushee,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "North Carolina"
        },
{
          "callsign": "Vern Buchanan",
          "alias": "Vern Buchanan,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Florida"
        },
{
          "callsign": "Veronica Escobar",
          "alias": "Veronica Escobar,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Texas"
        },
{
          "callsign": "Vicente Gonzalez Jr.",
          "alias": "Vicente Gonzalez Jr.,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Texas"
        },
{
          "callsign": "Victoria Spartz",
          "alias": "Victoria Spartz,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Indiana"
        },
{
          "callsign": "Virginia Foxx",
          "alias": "Virginia Foxx,

          "corpro": "",
          "frame": "Republican ",
          "mech": "North Carolina"
        },
{
          "callsign": "Warren Davidson",
          "alias": "Warren Davidson,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Ohio"
        },
{
          "callsign": "Wesley Hunt",
          "alias": "Wesley Hunt,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Texas"
        },
{
          "callsign": "Wiley Nickel",
          "alias": "Wiley Nickel,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "North Carolina"
        },
{
          "callsign": "William Timmons",
          "alias": "William Timmons,

          "corpro": "",
          "frame": "Republican ",
          "mech": "South Carolina"
        },
{
          "callsign": "Yadira Caraveo",
          "alias": "Yadira Caraveo,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "Colorado"
        },
{
          "callsign": "Young Kim",
          "alias": "Young Kim,

          "corpro": "",
          "frame": "Republican ",
          "mech": "California"
        },
{
          "callsign": "Yvette D. Clarke",
          "alias": "Yvette D. Clarke,

          "corpro": "",
          "frame": "Democratic ",
          "mech": "New York"
        },
{
          "callsign": "Zach Nunn",
          "alias": "Zach Nunn,

          "corpro": "",
          "frame": "Republican ",
          "mech": "Iowa"
        },
{
          "callsign": "Zoe Lofgren",
          "alias": "Zoe Lofgren,

          "corpro": "",
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
  width: 1902px;
  height: 910px;
  overflow: hidden;
}
</style>