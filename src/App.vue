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
          ""callsign"": ""Aaron"",
          ""alias"": ""Aaron Bean"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Republican "",
          ""mech"": ""Florida""
        },
{
          ""callsign"": ""Abigail"",
          ""alias"": ""Abigail Spanberger"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Democratic "",
          ""mech"": ""Virginia""
        },
{
          ""callsign"": ""Adam"",
          ""alias"": ""Adam Schiff"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Democratic "",
          ""mech"": ""California""
        },
{
          ""callsign"": ""Adrian"",
          ""alias"": ""Adrian Smith"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Republican "",
          ""mech"": ""Nebraska""
        },
{
          ""callsign"": ""Adriano"",
          ""alias"": ""Adriano Espaillat"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Democratic "",
          ""mech"": ""New York""
        },
{
          ""callsign"": ""Al"",
          ""alias"": ""Al Green"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Democratic "",
          ""mech"": ""Texas""
        },
{
          ""callsign"": ""Alexander"",
          ""alias"": ""Alexander Mooney"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Republican "",
          ""mech"": ""West Virginia""
        },
{
          ""callsign"": ""Alexandria"",
          ""alias"": ""Alexandria Ocasio-Cortez"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Democratic "",
          ""mech"": ""New York""
        },
{
          ""callsign"": ""Alma"",
          ""alias"": ""Alma Adams"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Democratic "",
          ""mech"": ""North Carolina""
        },
{
          ""callsign"": ""Ami"",
          ""alias"": ""Ami Bera"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Democratic "",
          ""mech"": ""California""
        },
{
          ""callsign"": ""André"",
          ""alias"": ""André Carson"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Democratic "",
          ""mech"": ""Indiana""
        },
{
          ""callsign"": ""Andrea"",
          ""alias"": ""Andrea Salinas"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Democratic "",
          ""mech"": ""Oregon""
        },
{
          ""callsign"": ""Andrew"",
          ""alias"": ""Andrew Clyde"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Republican "",
          ""mech"": ""Georgia""
        },
{
          ""callsign"": ""Andrew"",
          ""alias"": ""Andrew Garbarino"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Republican "",
          ""mech"": ""New York""
        },
{
          ""callsign"": ""Andrew"",
          ""alias"": ""Andrew Harris"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Republican "",
          ""mech"": ""Maryland""
        },
{
          ""callsign"": ""Andrew"",
          ""alias"": ""Andrew Kim"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Democratic "",
          ""mech"": ""New Jersey""
        },
{
          ""callsign"": ""Andy"",
          ""alias"": ""Andy Barr"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Republican "",
          ""mech"": ""Kentucky""
        },
{
          ""callsign"": ""Andy"",
          ""alias"": ""Andy Biggs"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Republican "",
          ""mech"": ""Arizona""
        },
{
          ""callsign"": ""Andy"",
          ""alias"": ""Andy Ogles"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Republican "",
          ""mech"": ""Tennessee""
        },
{
          ""callsign"": ""Angie"",
          ""alias"": ""Angie Craig"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Democratic "",
          ""mech"": ""Minnesota""
        },
{
          ""callsign"": ""Ann"",
          ""alias"": ""Ann Wagner"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Republican "",
          ""mech"": ""Missouri""
        },
{
          ""callsign"": ""Anna"",
          ""alias"": ""Anna Eshoo"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Democratic "",
          ""mech"": ""California""
        },
{
          ""callsign"": ""Anna"",
          ""alias"": ""Anna Paulina Luna"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Florida""
        },
{
          ""callsign"": ""Annie"",
          ""alias"": ""Annie Kuster"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Democratic "",
          ""mech"": ""New Hampshire""
        },
{
          ""callsign"": ""Anthony"",
          ""alias"": ""Anthony D'Esposito"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Republican "",
          ""mech"": ""New York""
        },
{
          ""callsign"": ""Ashley"",
          ""alias"": ""Ashley Hinson"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Republican "",
          ""mech"": ""Iowa""
        },
{
          ""callsign"": ""August"",
          ""alias"": ""August Pfluger"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Republican "",
          ""mech"": ""Texas""
        },
{
          ""callsign"": ""Aumua"",
          ""alias"": ""Aumua Amata Radewagen"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Republican "",
          ""mech"": ""American Samoa""
        },
{
          ""callsign"": ""Austin"",
          ""alias"": ""Austin Scott"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Republican "",
          ""mech"": ""Georgia""
        },
{
          ""callsign"": ""Ayanna"",
          ""alias"": ""Ayanna Pressley"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Democratic "",
          ""mech"": ""Massachusetts""
        },
{
          ""callsign"": ""Barbara"",
          ""alias"": ""Barbara Lee"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Democratic "",
          ""mech"": ""California""
        },
{
          ""callsign"": ""Barry"",
          ""alias"": ""Barry Loudermilk"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Republican "",
          ""mech"": ""Georgia""
        },
{
          ""callsign"": ""Barry"",
          ""alias"": ""Barry Moore"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Republican "",
          ""mech"": ""Alabama""
        },
{
          ""callsign"": ""Becca"",
          ""alias"": ""Becca Balint"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Vermont""
        },
{
          ""callsign"": ""Benjamin"",
          ""alias"": ""Benjamin Lee Cline"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Republican "",
          ""mech"": ""Virginia""
        },
{
          ""callsign"": ""Bennie"",
          ""alias"": ""Bennie Thompson"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Democratic "",
          ""mech"": ""Mississippi""
        },
{
          ""callsign"": ""Beth"",
          ""alias"": ""Beth Van Duyne"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Republican "",
          ""mech"": ""Texas""
        },
{
          ""callsign"": ""Betty"",
          ""alias"": ""Betty McCollum"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Democratic "",
          ""mech"": ""Minnesota""
        },
{
          ""callsign"": ""Bill"",
          ""alias"": ""Bill Foster"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Democratic "",
          ""mech"": ""Illinois""
        },
{
          ""callsign"": ""Bill"",
          ""alias"": ""Bill Huizenga"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Republican "",
          ""mech"": ""Michigan""
        },
{
          ""callsign"": ""Bill"",
          ""alias"": ""Bill Johnson"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Republican "",
          ""mech"": ""Ohio""
        },
{
          ""callsign"": ""Bill"",
          ""alias"": ""Bill Keating"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Democratic "",
          ""mech"": ""Massachusetts""
        },
{
          ""callsign"": ""Bill"",
          ""alias"": ""Bill Pascrell"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""New Jersey""
        },
{
          ""callsign"": ""Bill"",
          ""alias"": ""Bill Posey"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Republican "",
          ""mech"": ""Florida""
        },
{
          ""callsign"": ""Blaine"",
          ""alias"": ""Blaine Luetkemeyer"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Republican "",
          ""mech"": ""Missouri""
        },
{
          ""callsign"": ""Blake"",
          ""alias"": ""Blake Moore"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Republican "",
          ""mech"": ""Utah""
        },
{
          ""callsign"": ""Bob"",
          ""alias"": ""Bob Good"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Republican "",
          ""mech"": ""Virginia""
        },
{
          ""callsign"": ""Bob"",
          ""alias"": ""Bob Latta"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Republican "",
          ""mech"": ""Ohio""
        },
{
          ""callsign"": ""Bonnie"",
          ""alias"": ""Bonnie Watson Coleman"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Democratic "",
          ""mech"": ""New Jersey""
        },
{
          ""callsign"": ""Brad"",
          ""alias"": ""Brad Finstad"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Republican "",
          ""mech"": ""Minnesota""
        },
{
          ""callsign"": ""Brad"",
          ""alias"": ""Brad Schneider"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Democratic "",
          ""mech"": ""Illinois""
        },
{
          ""callsign"": ""Brad"",
          ""alias"": ""Brad Sherman"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Democratic "",
          ""mech"": ""California""
        },
{
          ""callsign"": ""Brad"",
          ""alias"": ""Brad Wenstrup"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Republican "",
          ""mech"": ""Ohio""
        },
{
          ""callsign"": ""Brandon"",
          ""alias"": ""Brandon Williams"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""New York""
        },
{
          ""callsign"": ""Brendan"",
          ""alias"": ""Brendan Boyle"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Pennsylvania""
        },
{
          ""callsign"": ""Brett"",
          ""alias"": ""Brett Guthrie"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Republican "",
          ""mech"": ""Kentucky""
        },
{
          ""callsign"": ""Brian"",
          ""alias"": ""Brian Babin"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Republican "",
          ""mech"": ""Texas""
        },
{
          ""callsign"": ""Brian"",
          ""alias"": ""Brian Fitzpatrick"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Republican "",
          ""mech"": ""Pennsylvania""
        },
{
          ""callsign"": ""Brian"",
          ""alias"": ""Brian Higgins"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Democratic "",
          ""mech"": ""New York""
        },
{
          ""callsign"": ""Brian"",
          ""alias"": ""Brian Mast"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Republican "",
          ""mech"": ""Florida""
        },
{
          ""callsign"": ""Brittany"",
          ""alias"": ""Brittany Pettersen"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Democratic "",
          ""mech"": ""Colorado""
        },
{
          ""callsign"": ""Bruce"",
          ""alias"": ""Bruce Westerman"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Republican "",
          ""mech"": ""Arkansas""
        },
{
          ""callsign"": ""Bryan"",
          ""alias"": ""Bryan Steil"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Republican "",
          ""mech"": ""Wisconsin""
        },
{
          ""callsign"": ""Burgess"",
          ""alias"": ""Burgess Owens"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Republican "",
          ""mech"": ""Utah""
        },
{
          ""callsign"": ""Byron"",
          ""alias"": ""Byron Donalds"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Republican "",
          ""mech"": ""Florida""
        },
{
          ""callsign"": ""Carlos"",
          ""alias"": ""Carlos Gimenez"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Republican "",
          ""mech"": ""Florida""
        },
{
          ""callsign"": ""Carol"",
          ""alias"": ""Carol Miller"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Republican "",
          ""mech"": ""West Virginia""
        },
{
          ""callsign"": ""Cathy"",
          ""alias"": ""Cathy McMorris Rodgers"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Republican "",
          ""mech"": ""Washington""
        },
{
          ""callsign"": ""Charles"",
          ""alias"": ""Charles J. Fleischmann"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Republican "",
          ""mech"": ""Tennessee""
        },
{
          ""callsign"": ""Chellie"",
          ""alias"": ""Chellie Pingree"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Democratic "",
          ""mech"": ""Maine""
        },
{
          ""callsign"": ""Chip"",
          ""alias"": ""Chip Roy"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Republican "",
          ""mech"": ""Texas""
        },
{
          ""callsign"": ""Chris"",
          ""alias"": ""Chris Pappas"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Democratic "",
          ""mech"": ""New Hampshire""
        },
{
          ""callsign"": ""Chris"",
          ""alias"": ""Chris Smith"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Republican "",
          ""mech"": ""New Jersey""
        },
{
          ""callsign"": ""Chris"",
          ""alias"": ""Chris Stewart"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Republican "",
          ""mech"": ""Utah""
        },
{
          ""callsign"": ""Chrissy"",
          ""alias"": ""Chrissy Houlahan"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Democratic "",
          ""mech"": ""Pennsylvania""
        },
{
          ""callsign"": ""Christopher"",
          ""alias"": ""Christopher Deluzio"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Democratic "",
          ""mech"": ""Pennsylvania""
        },
{
          ""callsign"": ""Chuck"",
          ""alias"": ""Chuck Edwards"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Republican "",
          ""mech"": ""North Carolina""
        },
{
          ""callsign"": ""Claudia"",
          ""alias"": ""Claudia Tenney"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Republican "",
          ""mech"": ""New York""
        },
{
          ""callsign"": ""Clay"",
          ""alias"": ""Clay Higgins"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Republican "",
          ""mech"": ""Louisiana""
        },
{
          ""callsign"": ""Cliff"",
          ""alias"": ""Cliff Bentz"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Republican "",
          ""mech"": ""Oregon""
        },
{
          ""callsign"": ""Colin"",
          ""alias"": ""Colin Allred"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Democratic "",
          ""mech"": ""Texas""
        },
{
          ""callsign"": ""Cori"",
          ""alias"": ""Cori Bush"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Democratic "",
          ""mech"": ""Missouri""
        },
{
          ""callsign"": ""Cory"",
          ""alias"": ""Cory Mills"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Republican "",
          ""mech"": ""Florida""
        },
{
          ""callsign"": ""D."",
          ""alias"": ""D. Adam Smith"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Democratic "",
          ""mech"": ""Washington""
        },
{
          ""callsign"": ""Dale"",
          ""alias"": ""Dale Strong"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Republican "",
          ""mech"": ""Alabama""
        },
{
          ""callsign"": ""Dan"",
          ""alias"": ""Dan Bishop"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Republican "",
          ""mech"": ""North Carolina""
        },
{
          ""callsign"": ""Dan"",
          ""alias"": ""Dan Kildee"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Democratic "",
          ""mech"": ""Michigan""
        },
{
          ""callsign"": ""Dan"",
          ""alias"": ""Dan Meuser"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Republican "",
          ""mech"": ""Pennsylvania""
        },
{
          ""callsign"": ""Dan"",
          ""alias"": ""Dan Newhouse"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Republican "",
          ""mech"": ""Washington""
        },
{
          ""callsign"": ""Daniel"",
          ""alias"": ""Daniel Crenshaw"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Republican "",
          ""mech"": ""Texas""
        },
{
          ""callsign"": ""Daniel"",
          ""alias"": ""Daniel Goldman"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Democratic "",
          ""mech"": ""New York""
        },
{
          ""callsign"": ""Daniel"",
          ""alias"": ""Daniel Webster"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Republican "",
          ""mech"": ""Florida""
        },
{
          ""callsign"": ""Danny"",
          ""alias"": ""Danny K. Davis"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Democratic "",
          ""mech"": ""Illinois""
        },
{
          ""callsign"": ""Darin"",
          ""alias"": ""Darin LaHood"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Republican "",
          ""mech"": ""Illinois""
        },
{
          ""callsign"": ""Darrell"",
          ""alias"": ""Darrell Issa"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Republican "",
          ""mech"": ""California""
        },
{
          ""callsign"": ""Darren"",
          ""alias"": ""Darren Soto"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Democratic "",
          ""mech"": ""Florida""
        },
{
          ""callsign"": ""David"",
          ""alias"": ""David G. Valadao"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Republican "",
          ""mech"": ""California""
        },
{
          ""callsign"": ""David"",
          ""alias"": ""David Joyce"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Republican "",
          ""mech"": ""Ohio""
        },
{
          ""callsign"": ""David"",
          ""alias"": ""David Kustoff"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Republican "",
          ""mech"": ""Tennessee""
        },
{
          ""callsign"": ""David"",
          ""alias"": ""David N. Cicilline"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Democratic "",
          ""mech"": ""Rhode Island""
        },
{
          ""callsign"": ""David"",
          ""alias"": ""David Rouzer"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Republican "",
          ""mech"": ""North Carolina""
        },
{
          ""callsign"": ""David"",
          ""alias"": ""David Schweikert"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Republican "",
          ""mech"": ""Arizona""
        },
{
          ""callsign"": ""David"",
          ""alias"": ""David Scott"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Democratic "",
          ""mech"": ""Georgia""
        },
{
          ""callsign"": ""David"",
          ""alias"": ""David Trone"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Democratic "",
          ""mech"": ""Maryland""
        },
{
          ""callsign"": ""Dean"",
          ""alias"": ""Dean Phillips"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Democratic "",
          ""mech"": ""Minnesota""
        },
{
          ""callsign"": ""Debbie"",
          ""alias"": ""Debbie Dingell"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Democratic "",
          ""mech"": ""Michigan""
        },
{
          ""callsign"": ""Debbie"",
          ""alias"": ""Debbie Lesko"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Republican "",
          ""mech"": ""Arizona""
        },
{
          ""callsign"": ""Debbie"",
          ""alias"": ""Debbie Wasserman Schultz"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Democratic "",
          ""mech"": ""Florida""
        },
{
          ""callsign"": ""Deborah"",
          ""alias"": ""Deborah Ross"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Democratic "",
          ""mech"": ""North Carolina""
        },
{
          ""callsign"": ""Delia"",
          ""alias"": ""Delia Ramirez"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Democratic "",
          ""mech"": ""Illinois""
        },
{
          ""callsign"": ""Derek"",
          ""alias"": ""Derek Kilmer"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Democratic "",
          ""mech"": ""Washington""
        },
{
          ""callsign"": ""Derrick"",
          ""alias"": ""Derrick Van Orden"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Republican "",
          ""mech"": ""Wisconsin""
        },
{
          ""callsign"": ""Diana"",
          ""alias"": ""Diana DeGette"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Democratic "",
          ""mech"": ""Colorado""
        },
{
          ""callsign"": ""Diana"",
          ""alias"": ""Diana Harshbarger"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Republican "",
          ""mech"": ""Tennessee""
        },
{
          ""callsign"": ""Dina"",
          ""alias"": ""Dina Titus"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Democratic "",
          ""mech"": ""Nevada""
        },
{
          ""callsign"": ""Don"",
          ""alias"": ""Don Bacon"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Republican "",
          ""mech"": ""Nebraska""
        },
{
          ""callsign"": ""Donald"",
          ""alias"": ""Donald Davis"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Democratic "",
          ""mech"": ""North Carolina""
        },
{
          ""callsign"": ""Donald"",
          ""alias"": ""Donald Norcross"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Democratic "",
          ""mech"": ""New Jersey""
        },
{
          ""callsign"": ""Donald"",
          ""alias"": ""Donald Payne Jr."",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Democratic "",
          ""mech"": ""New Jersey""
        },
{
          ""callsign"": ""Donald"",
          ""alias"": ""Donald Sternoff Beyer Jr."",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Democratic "",
          ""mech"": ""Virginia""
        },
{
          ""callsign"": ""Doris"",
          ""alias"": ""Doris Matsui"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Democratic "",
          ""mech"": ""California""
        },
{
          ""callsign"": ""Doug"",
          ""alias"": ""Doug LaMalfa"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Republican "",
          ""mech"": ""California""
        },
{
          ""callsign"": ""Doug"",
          ""alias"": ""Doug Lamborn"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Republican "",
          ""mech"": ""Colorado""
        },
{
          ""callsign"": ""Drew"",
          ""alias"": ""Drew Ferguson"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Republican "",
          ""mech"": ""Georgia""
        },
{
          ""callsign"": ""Dusty"",
          ""alias"": ""Dusty Johnson"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Republican "",
          ""mech"": ""South Dakota""
        },
{
          ""callsign"": ""Dutch"",
          ""alias"": ""Dutch Ruppersberger"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Democratic "",
          ""mech"": ""Maryland""
        },
{
          ""callsign"": ""Dwight"",
          ""alias"": ""Dwight Evans"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Democratic "",
          ""mech"": ""Pennsylvania""
        },
{
          ""callsign"": ""Earl"",
          ""alias"": ""Earl Blumenauer"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Democratic "",
          ""mech"": ""Oregon""
        },
{
          ""callsign"": ""Earl"",
          ""alias"": ""Earl Carter"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Republican "",
          ""mech"": ""Georgia""
        },
{
          ""callsign"": ""Ed"",
          ""alias"": ""Ed Case"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Democratic "",
          ""mech"": ""Hawaii""
        },
{
          ""callsign"": ""Eleanor"",
          ""alias"": ""Eleanor Holmes Norton"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Democratic "",
          ""mech"": ""Non-Voting""
        },
{
          ""callsign"": ""Eli"",
          ""alias"": ""Eli Crane"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Republican "",
          ""mech"": ""Arizona""
        },
{
          ""callsign"": ""Elise"",
          ""alias"": ""Elise Stefanik"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Republican "",
          ""mech"": ""New York""
        },
{
          ""callsign"": ""Elissa"",
          ""alias"": ""Elissa Slotkin"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Democratic "",
          ""mech"": ""Michigan""
        },
{
          ""callsign"": ""Emanuel"",
          ""alias"": ""Emanuel Cleaver"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Democratic "",
          ""mech"": ""Missouri""
        },
{
          ""callsign"": ""Emilia"",
          ""alias"": ""Emilia Sykes"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Democratic "",
          ""mech"": ""Ohio""
        },
{
          ""callsign"": ""Eric"",
          ""alias"": ""Eric Burlison"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Republican "",
          ""mech"": ""Missouri""
        },
{
          ""callsign"": ""Eric"",
          ""alias"": ""Eric Sorensen"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Democratic "",
          ""mech"": ""Illinois""
        },
{
          ""callsign"": ""Eric"",
          ""alias"": ""Eric Swalwell"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Democratic "",
          ""mech"": ""California""
        },
{
          ""callsign"": ""Erin"",
          ""alias"": ""Erin Houchin"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Republican "",
          ""mech"": ""Indiana""
        },
{
          ""callsign"": ""Frank"",
          ""alias"": ""Frank Lucas"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Republican "",
          ""mech"": ""Oklahoma""
        },
{
          ""callsign"": ""Frank"",
          ""alias"": ""Frank Mrvan"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Democratic "",
          ""mech"": ""Indiana""
        },
{
          ""callsign"": ""Frank"",
          ""alias"": ""Frank Pallone Jr."",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Democratic "",
          ""mech"": ""New Jersey""
        },
{
          ""callsign"": ""Frederica"",
          ""alias"": ""Frederica S. Wilson"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Democratic "",
          ""mech"": ""Florida""
        },
{
          ""callsign"": ""French"",
          ""alias"": ""French Hill"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Republican "",
          ""mech"": ""Arkansas""
        },
{
          ""callsign"": ""Gabriel"",
          ""alias"": ""Gabriel Vasquez"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Democratic "",
          ""mech"": ""New Mexico""
        },
{
          ""callsign"": ""Garret"",
          ""alias"": ""Garret Graves"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Republican "",
          ""mech"": ""Louisiana""
        },
{
          ""callsign"": ""Gary"",
          ""alias"": ""Gary Palmer"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Republican "",
          ""mech"": ""Alabama""
        },
{
          ""callsign"": ""George"",
          ""alias"": ""George Devolder-Santos"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""New York""
        },
{
          ""callsign"": ""Gerald"",
          ""alias"": ""Gerald Edward Connolly"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Virginia""
        },
{
          ""callsign"": ""Glenn"",
          ""alias"": ""Glenn Grothman"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Republican "",
          ""mech"": ""Wisconsin""
        },
{
          ""callsign"": ""Glenn"",
          ""alias"": ""Glenn Ivey"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Democratic "",
          ""mech"": ""Maryland""
        },
{
          ""callsign"": ""Glenn"",
          ""alias"": ""Glenn Thompson"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": ""Available"",
          ""frame"": ""Republican "",
          ""mech"": ""Pennsylvania""
        },

{
          ""callsign"": ""Grace"",
          ""alias"": ""Grace Napolitano"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""California""
        },
{
          ""callsign"": ""Greg"",
          ""alias"": ""Greg Casar"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Texas""
        },
{
          ""callsign"": ""Greg"",
          ""alias"": ""Greg Landsman"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Ohio""
        },
{
          ""callsign"": ""Greg"",
          ""alias"": ""Greg Pence"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Indiana""
        },
{
          ""callsign"": ""Greg"",
          ""alias"": ""Greg Stanton"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Arizona""
        },
{
          ""callsign"": ""Greg"",
          ""alias"": ""Greg Steube"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Florida""
        },
{
          ""callsign"": ""Gregorio"",
          ""alias"": ""Gregorio Kilili Camacho Sablan"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Northern Mariana Islands""
        },
{
          ""callsign"": ""Gregory"",
          ""alias"": ""Gregory Murphy"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""North Carolina""
        },
{
          ""callsign"": ""Gregory"",
          ""alias"": ""Gregory W. Meeks"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""New York""
        },
{
          ""callsign"": ""Gus"",
          ""alias"": ""Gus M. Bilirakis"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Florida""
        },
{
          ""callsign"": ""Guy"",
          ""alias"": ""Guy Reschenthaler"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Pennsylvania""
        },
{
          ""callsign"": ""Gwen"",
          ""alias"": ""Gwen Moore"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Wisconsin""
        },
{
          ""callsign"": ""H."",
          ""alias"": ""H. Morgan Griffith"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Virginia""
        },
{
          ""callsign"": ""Hakeem"",
          ""alias"": ""Hakeem Jeffries"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""New York""
        },
{
          ""callsign"": ""Hal"",
          ""alias"": ""Hal Rogers"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Kentucky""
        },
{
          ""callsign"": ""Haley"",
          ""alias"": ""Haley Stevens"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Michigan""
        },
{
          ""callsign"": ""Hank"",
          ""alias"": ""Hank Johnson"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Georgia""
        },
{
          ""callsign"": ""Harriet"",
          ""alias"": ""Harriet Hageman"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Wyoming""
        },
{
          ""callsign"": ""Henry"",
          ""alias"": ""Henry Cuellar"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Texas""
        },
{
          ""callsign"": ""Hillary"",
          ""alias"": ""Hillary Scholten"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Michigan""
        },
{
          ""callsign"": ""Ilhan"",
          ""alias"": ""Ilhan Omar"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Minnesota""
        },
{
          ""callsign"": ""Jack"",
          ""alias"": ""Jack Bergman"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Michigan""
        },
{
          ""callsign"": ""Jacob"",
          ""alias"": ""Jacob LaTurner"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Kansas""
        },
{
          ""callsign"": ""Jahana"",
          ""alias"": ""Jahana Hayes"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Connecticut""
        },
{
          ""callsign"": ""Jake"",
          ""alias"": ""Jake Auchincloss"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Massachusetts""
        },
{
          ""callsign"": ""Jake"",
          ""alias"": ""Jake Ellzey"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Texas""
        },
{
          ""callsign"": ""Jamaal"",
          ""alias"": ""Jamaal Bowman"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""New York""
        },
{
          ""callsign"": ""James"",
          ""alias"": ""James Clyburn"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""South Carolina""
        },
{
          ""callsign"": ""James"",
          ""alias"": ""James Comer Jr."",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Kentucky""
        },
{
          ""callsign"": ""James"",
          ""alias"": ""James Moylan"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Guam""
        },
{
          ""callsign"": ""Jamie"",
          ""alias"": ""Jamie Raskin"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Maryland""
        },
{
          ""callsign"": ""Jan"",
          ""alias"": ""Jan Schakowsky"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Illinois""
        },
{
          ""callsign"": ""Jared"",
          ""alias"": ""Jared Evan Moskowitz"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Florida""
        },
{
          ""callsign"": ""Jared"",
          ""alias"": ""Jared Golden"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Maine""
        },
{
          ""callsign"": ""Jared"",
          ""alias"": ""Jared Huffman"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""California""
        },
{
          ""callsign"": ""Jasmine"",
          ""alias"": ""Jasmine Crockett"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Texas""
        },
{
          ""callsign"": ""Jason"",
          ""alias"": ""Jason Crow"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Colorado""
        },
{
          ""callsign"": ""Jason"",
          ""alias"": ""Jason Smith"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Missouri""
        },
{
          ""callsign"": ""Jay"",
          ""alias"": ""Jay Obernolte"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""California""
        },
{
          ""callsign"": ""Jeff"",
          ""alias"": ""Jeff Duncan"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""South Carolina""
        },
{
          ""callsign"": ""Jeff"",
          ""alias"": ""Jeff Jackson"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""North Carolina""
        },
{
          ""callsign"": ""Jeff"",
          ""alias"": ""Jeff Van Drew"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""New Jersey""
        },
{
          ""callsign"": ""Jennifer"",
          ""alias"": ""Jennifer Kiggans"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Virginia""
        },
{
          ""callsign"": ""Jennifer"",
          ""alias"": ""Jennifer McClellan"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Virginia""
        },
{
          ""callsign"": ""Jennifer"",
          ""alias"": ""Jennifer Wexton"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Virginia""
        },
{
          ""callsign"": ""Jerrold"",
          ""alias"": ""Jerrold Nadler"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""New York""
        },
{
          ""callsign"": ""Jerry"",
          ""alias"": ""Jerry Carl"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Alabama""
        },
{
          ""callsign"": ""Jesus"",
          ""alias"": ""Jesus Garcia"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Illinois""
        },
{
          ""callsign"": ""Jill"",
          ""alias"": ""Jill Tokuda"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Hawaii""
        },
{
          ""callsign"": ""Jim"",
          ""alias"": ""Jim Baird"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Indiana""
        },
{
          ""callsign"": ""Jim"",
          ""alias"": ""Jim Banks"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Indiana""
        },
{
          ""callsign"": ""Jim"",
          ""alias"": ""Jim Costa"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""California""
        },
{
          ""callsign"": ""Jim"",
          ""alias"": ""Jim Himes"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Connecticut""
        },
{
          ""callsign"": ""Jim"",
          ""alias"": ""Jim Jordan"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Ohio""
        },
{
          ""callsign"": ""Jim"",
          ""alias"": ""Jim McGovern"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Massachusetts""
        },
{
          ""callsign"": ""Jimmy"",
          ""alias"": ""Jimmy Gomez"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""California""
        },
{
          ""callsign"": ""Jimmy"",
          ""alias"": ""Jimmy Panetta"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""California""
        },
{
          ""callsign"": ""Joaquin"",
          ""alias"": ""Joaquin Castro"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Texas""
        },
{
          ""callsign"": ""Jodey"",
          ""alias"": ""Jodey Arrington"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Texas""
        },
{
          ""callsign"": ""Joe"",
          ""alias"": ""Joe Courtney"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Connecticut""
        },
{
          ""callsign"": ""Joe"",
          ""alias"": ""Joe Neguse"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Colorado""
        },
{
          ""callsign"": ""Joe"",
          ""alias"": ""Joe Wilson"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""South Carolina""
        },
{
          ""callsign"": ""John"",
          ""alias"": ""John Carter"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Texas""
        },
{
          ""callsign"": ""John"",
          ""alias"": ""John Curtis"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Utah""
        },
{
          ""callsign"": ""John"",
          ""alias"": ""John Duarte"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""California""
        },
{
          ""callsign"": ""John"",
          ""alias"": ""John Garamendi"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""California""
        },
{
          ""callsign"": ""John"",
          ""alias"": ""John James"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Michigan""
        },
{
          ""callsign"": ""John"",
          ""alias"": ""John Joyce"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Pennsylvania""
        },
{
          ""callsign"": ""John"",
          ""alias"": ""John Larson"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Connecticut""
        },
{
          ""callsign"": ""John"",
          ""alias"": ""John Moolenaar"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Michigan""
        },
{
          ""callsign"": ""John"",
          ""alias"": ""John Rose"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Tennessee""
        },
{
          ""callsign"": ""John"",
          ""alias"": ""John Rutherford"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Florida""
        },
{
          ""callsign"": ""John"",
          ""alias"": ""John Sarbanes"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Maryland""
        },
{
          ""callsign"": ""Jonathan"",
          ""alias"": ""Jonathan Jackson"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Illinois""
        },
{
          ""callsign"": ""Joseph"",
          ""alias"": ""Joseph Morelle"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""New York""
        },
{
          ""callsign"": ""Josh"",
          ""alias"": ""Josh Brecheen"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Oklahoma""
        },
{
          ""callsign"": ""Josh"",
          ""alias"": ""Josh Gottheimer"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""New Jersey""
        },
{
          ""callsign"": ""Josh"",
          ""alias"": ""Josh Harder"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""California""
        },
{
          ""callsign"": ""Joyce"",
          ""alias"": ""Joyce Beatty"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Ohio""
        },
{
          ""callsign"": ""Juan"",
          ""alias"": ""Juan Ciscomani"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Arizona""
        },
{
          ""callsign"": ""Juan"",
          ""alias"": ""Juan Vargas"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""California""
        },
{
          ""callsign"": ""Judy"",
          ""alias"": ""Judy Chu"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""California""
        },
{
          ""callsign"": ""Julia"",
          ""alias"": ""Julia Brownley"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""California""
        },
{
          ""callsign"": ""Julia"",
          ""alias"": ""Julia Letlow"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Louisiana""
        },
{
          ""callsign"": ""Kat"",
          ""alias"": ""Kat Cammack"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Florida""
        },
{
          ""callsign"": ""Katherine"",
          ""alias"": ""Katherine Clark"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Massachusetts""
        },
{
          ""callsign"": ""Kathy"",
          ""alias"": ""Kathy Castor"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Florida""
        },
{
          ""callsign"": ""Kathy"",
          ""alias"": ""Kathy Manning"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""North Carolina""
        },
{
          ""callsign"": ""Katie"",
          ""alias"": ""Katie Porter"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""California""
        },
{
          ""callsign"": ""Kay"",
          ""alias"": ""Kay Granger"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Texas""
        },
{
          ""callsign"": ""Keith"",
          ""alias"": ""Keith Self"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Texas""
        },
{
          ""callsign"": ""Kelly"",
          ""alias"": ""Kelly Armstrong"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""North Dakota""
        },
{
          ""callsign"": ""Ken"",
          ""alias"": ""Ken Buck"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Colorado""
        },
{
          ""callsign"": ""Ken"",
          ""alias"": ""Ken Calvert"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""California""
        },
{
          ""callsign"": ""Kevin"",
          ""alias"": ""Kevin Hern"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Oklahoma""
        },
{
          ""callsign"": ""Kevin"",
          ""alias"": ""Kevin Kiley"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""California""
        },
{
          ""callsign"": ""Kevin"",
          ""alias"": ""Kevin McCarthy"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""California""
        },
{
          ""callsign"": ""Kevin"",
          ""alias"": ""Kevin Mullin"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""California""
        },
{
          ""callsign"": ""Kim"",
          ""alias"": ""Kim Schrier"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Washington""
        },
{
          ""callsign"": ""Kweisi"",
          ""alias"": ""Kweisi Mfume"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Maryland""
        },
{
          ""callsign"": ""Lance"",
          ""alias"": ""Lance Gooden"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Texas""
        },
{
          ""callsign"": ""Larry"",
          ""alias"": ""Larry Bucshon"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Indiana""
        },
{
          ""callsign"": ""Laurel"",
          ""alias"": ""Laurel Lee"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Florida""
        },
{
          ""callsign"": ""Lauren"",
          ""alias"": ""Lauren Boebert"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Colorado""
        },
{
          ""callsign"": ""Lauren"",
          ""alias"": ""Lauren Underwood"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Illinois""
        },
{
          ""callsign"": ""Linda"",
          ""alias"": ""Linda Sánchez"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""California""
        },
{
          ""callsign"": ""Lisa"",
          ""alias"": ""Lisa Blunt Rochester"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Delaware""
        },
{
          ""callsign"": ""Lisa"",
          ""alias"": ""Lisa McClain"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Michigan""
        },
{
          ""callsign"": ""Lizzie"",
          ""alias"": ""Lizzie Pannill Fletcher"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Texas""
        },
{
          ""callsign"": ""Lloyd"",
          ""alias"": ""Lloyd Doggett"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Texas""
        },
{
          ""callsign"": ""Lloyd"",
          ""alias"": ""Lloyd Smucker"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Pennsylvania""
        },
{
          ""callsign"": ""Lois"",
          ""alias"": ""Lois Frankel"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Florida""
        },
{
          ""callsign"": ""Lori"",
          ""alias"": ""Lori Chavez-DeRemer"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Oregon""
        },
{
          ""callsign"": ""Lori"",
          ""alias"": ""Lori Trahan"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Massachusetts""
        },
{
          ""callsign"": ""Lou"",
          ""alias"": ""Lou Correa"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""California""
        },
{
          ""callsign"": ""Lucy"",
          ""alias"": ""Lucy McBath"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Georgia""
        },
{
          ""callsign"": ""Madeleine"",
          ""alias"": ""Madeleine Dean"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Pennsylvania""
        },
{
          ""callsign"": ""Marc"",
          ""alias"": ""Marc Veasey"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Texas""
        },
{
          ""callsign"": ""Marcus"",
          ""alias"": ""Marcus Molinaro"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""New York""
        },
{
          ""callsign"": ""Marcy"",
          ""alias"": ""Marcy Kaptur"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Ohio""
        },
{
          ""callsign"": ""Maria"",
          ""alias"": ""Maria Elvira Salazar"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Florida""
        },
{
          ""callsign"": ""Mariannette"",
          ""alias"": ""Mariannette Miller-Meeks"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Iowa""
        },
{
          ""callsign"": ""Marie"",
          ""alias"": ""Marie Gluesenkamp Pérez"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Washington""
        },
{
          ""callsign"": ""Marilyn"",
          ""alias"": ""Marilyn Strickland"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Washington""
        },
{
          ""callsign"": ""Mario"",
          ""alias"": ""Mario Diaz-Balart"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Florida""
        },
{
          ""callsign"": ""Marjorie"",
          ""alias"": ""Marjorie Taylor Greene"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Georgia""
        },
{
          ""callsign"": ""Mark"",
          ""alias"": ""Mark Alford"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Missouri""
        },
{
          ""callsign"": ""Mark"",
          ""alias"": ""Mark Amodei"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Nevada""
        },
{
          ""callsign"": ""Mark"",
          ""alias"": ""Mark DeSaulnier"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""California""
        },
{
          ""callsign"": ""Mark"",
          ""alias"": ""Mark Green"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Tennessee""
        },
{
          ""callsign"": ""Mark"",
          ""alias"": ""Mark Pocan"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Wisconsin""
        },
{
          ""callsign"": ""Mark"",
          ""alias"": ""Mark Takano"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""California""
        },
{
          ""callsign"": ""Mary"",
          ""alias"": ""Mary Gay Scanlon"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Pennsylvania""
        },
{
          ""callsign"": ""Mary"",
          ""alias"": ""Mary Miller"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Illinois""
        },
{
          ""callsign"": ""Mary"",
          ""alias"": ""Mary Peltola"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Alaska""
        },
{
          ""callsign"": ""Matt"",
          ""alias"": ""Matt Cartwright"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Pennsylvania""
        },
{
          ""callsign"": ""Matt"",
          ""alias"": ""Matt Gaetz"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Florida""
        },
{
          ""callsign"": ""Matt"",
          ""alias"": ""Matt Rosendale"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Montana""
        },
{
          ""callsign"": ""Max"",
          ""alias"": ""Max Miller"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Ohio""
        },
{
          ""callsign"": ""Maxine"",
          ""alias"": ""Maxine Waters"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""California""
        },
{
          ""callsign"": ""Maxwell"",
          ""alias"": ""Maxwell Alejandro Frost"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Florida""
        },
{
          ""callsign"": ""Melanie"",
          ""alias"": ""Melanie Ann Stansbury"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""New Mexico""
        },
{
          ""callsign"": ""Michael"",
          ""alias"": ""Michael C. Burgess"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Texas""
        },
{
          ""callsign"": ""Michael"",
          ""alias"": ""Michael Cloud"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Texas""
        },
{
          ""callsign"": ""Michael"",
          ""alias"": ""Michael Guest"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Mississippi""
        },
{
          ""callsign"": ""Michael"",
          ""alias"": ""Michael K. Simpson"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Idaho""
        },
{
          ""callsign"": ""Michael"",
          ""alias"": ""Michael Lawler"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""New York""
        },
{
          ""callsign"": ""Michael"",
          ""alias"": ""Michael McCaul"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Texas""
        },
{
          ""callsign"": ""Michael"",
          ""alias"": ""Michael Turner"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Ohio""
        },
{
          ""callsign"": ""Michael"",
          ""alias"": ""Michael Waltz"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Florida""
        },
{
          ""callsign"": ""Michelle"",
          ""alias"": ""Michelle Fischbach"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Minnesota""
        },
{
          ""callsign"": ""Michelle"",
          ""alias"": ""Michelle Steel"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""California""
        },
{
          ""callsign"": ""Mike"",
          ""alias"": ""Mike Bost"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Illinois""
        },
{
          ""callsign"": ""Mike"",
          ""alias"": ""Mike Carey"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Ohio""
        },
{
          ""callsign"": ""Mike"",
          ""alias"": ""Mike Collins"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Georgia""
        },
{
          ""callsign"": ""Mike"",
          ""alias"": ""Mike Ezell"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Mississippi""
        },
{
          ""callsign"": ""Mike"",
          ""alias"": ""Mike Flood"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Nebraska""
        },
{
          ""callsign"": ""Mike"",
          ""alias"": ""Mike Gallagher"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Wisconsin""
        },
{
          ""callsign"": ""Mike"",
          ""alias"": ""Mike Garcia"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""California""
        },
{
          ""callsign"": ""Mike"",
          ""alias"": ""Mike Johnson"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Louisiana""
        },
{
          ""callsign"": ""Mike"",
          ""alias"": ""Mike Kelly"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Pennsylvania""
        },
{
          ""callsign"": ""Mike"",
          ""alias"": ""Mike Levin"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""California""
        },
{
          ""callsign"": ""Mike"",
          ""alias"": ""Mike Quigley"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Illinois""
        },
{
          ""callsign"": ""Mike"",
          ""alias"": ""Mike Rogers"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Alabama""
        },
{
          ""callsign"": ""Mike"",
          ""alias"": ""Mike Thompson"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""California""
        },
{
          ""callsign"": ""Mikie"",
          ""alias"": ""Mikie Sherrill"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""New Jersey""
        },
{
          ""callsign"": ""Monica"",
          ""alias"": ""Monica De La Cruz"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Texas""
        },
{
          ""callsign"": ""Morgan"",
          ""alias"": ""Morgan Luttrell"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Texas""
        },
{
          ""callsign"": ""Morgan"",
          ""alias"": ""Morgan McGarvey"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Kentucky""
        },
{
          ""callsign"": ""Nancy"",
          ""alias"": ""Nancy Mace"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""South Carolina""
        },
{
          ""callsign"": ""Nancy"",
          ""alias"": ""Nancy Pelosi"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""California""
        },
{
          ""callsign"": ""Nanette"",
          ""alias"": ""Nanette Barragán"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""California""
        },
{
          ""callsign"": ""Nathaniel"",
          ""alias"": ""Nathaniel Moran"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Texas""
        },
{
          ""callsign"": ""Neal"",
          ""alias"": ""Neal Dunn"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Florida""
        },
{
          ""callsign"": ""Nicholas"",
          ""alias"": ""Nicholas A. Langworthy"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""New York""
        },
{
          ""callsign"": ""Nicholas"",
          ""alias"": ""Nicholas J. LaLota"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""New York""
        },
{
          ""callsign"": ""Nicole"",
          ""alias"": ""Nicole Malliotakis"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""New York""
        },
{
          ""callsign"": ""Nikema"",
          ""alias"": ""Nikema Williams"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Georgia""
        },
{
          ""callsign"": ""Nikki"",
          ""alias"": ""Nikki Budzinski"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Illinois""
        },
{
          ""callsign"": ""Norma"",
          ""alias"": ""Norma Torres"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""California""
        },
{
          ""callsign"": ""Nydia"",
          ""alias"": ""Nydia Velazquez"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""New""
        },
{
          ""callsign"": ""Pat"",
          ""alias"": ""Pat Fallon"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Texas""
        },
{
          ""callsign"": ""Pat"",
          ""alias"": ""Pat Ryan"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""New""
        },
{
          ""callsign"": ""Patrick"",
          ""alias"": ""Patrick T. McHenry"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""North Carolina""
        },
{
          ""callsign"": ""Paul"",
          ""alias"": ""Paul Gosar"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Arizona""
        },
{
          ""callsign"": ""Paul"",
          ""alias"": ""Paul Tonko"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""New York""
        },
{
          ""callsign"": ""Pete"",
          ""alias"": ""Pete Aguilar"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""California""
        },
{
          ""callsign"": ""Pete"",
          ""alias"": ""Pete Sessions"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Texas""
        },
{
          ""callsign"": ""Pete"",
          ""alias"": ""Pete Stauber"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Minnesota""
        },
{
          ""callsign"": ""Pramila"",
          ""alias"": ""Pramila Jayapal"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Washington""
        },
{
          ""callsign"": ""Raja"",
          ""alias"": ""Raja Krishnamoorthi"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Illinois""
        },
{
          ""callsign"": ""Ralph"",
          ""alias"": ""Ralph Norman"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""South Carolina""
        },
{
          ""callsign"": ""Randy"",
          ""alias"": ""Randy Feenstra"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Iowa""
        },
{
          ""callsign"": ""Randy"",
          ""alias"": ""Randy Weber"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Texas""
        },
{
          ""callsign"": ""Rashida"",
          ""alias"": ""Rashida Tlaib"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Michigan""
        },
{
          ""callsign"": ""Raúl"",
          ""alias"": ""Raúl Grijalva"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Arizona""
        },
{
          ""callsign"": ""Raul"",
          ""alias"": ""Raul Ruiz"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""California""
        },
{
          ""callsign"": ""Rich"",
          ""alias"": ""Rich McCormick"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Georgia""
        },
{
          ""callsign"": ""Richard"",
          ""alias"": ""Richard Hudson"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""North Carolina""
        },
{
          ""callsign"": ""Richard"",
          ""alias"": ""Richard Neal"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Massachusetts""
        },
{
          ""callsign"": ""Rick"",
          ""alias"": ""Rick Allen"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Georgia""
        },
{
          ""callsign"": ""Rick"",
          ""alias"": ""Rick Crawford"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Arkansas""
        },
{
          ""callsign"": ""Rick"",
          ""alias"": ""Rick Larsen"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Washington""
        },
{
          ""callsign"": ""Ritchie"",
          ""alias"": ""Ritchie Torres"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""New York""
        },
{
          ""callsign"": ""Ro"",
          ""alias"": ""Ro Khanna"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""California""
        },
{
          ""callsign"": ""Robert"",
          ""alias"": ""Robert Aderholt"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Alabama""
        },
{
          ""callsign"": ""Robert"",
          ""alias"": ""Robert C. Scott"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Virginia""
        },
{
          ""callsign"": ""Robert"",
          ""alias"": ""Robert Garcia"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""California""
        },
{
          ""callsign"": ""Robert"",
          ""alias"": ""Robert J. Wittman"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Virginia""
        },
{
          ""callsign"": ""Robert"",
          ""alias"": ""Robert Menendez Jr."",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""New Jersey""
        },
{
          ""callsign"": ""Robin"",
          ""alias"": ""Robin Kelly"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Illinois""
        },
{
          ""callsign"": ""Roger"",
          ""alias"": ""Roger Williams"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Texas""
        },
{
          ""callsign"": ""Ron"",
          ""alias"": ""Ron Estes"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Kansas""
        },
{
          ""callsign"": ""Ronny"",
          ""alias"": ""Ronny L. Jackson"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Texas""
        },
{
          ""callsign"": ""Rosa"",
          ""alias"": ""Rosa L. DeLauro"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Connecticut""
        },
{
          ""callsign"": ""Ruben"",
          ""alias"": ""Ruben Gallego"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Arizona""
        },
{
          ""callsign"": ""Rudy"",
          ""alias"": ""Rudy Yakym"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Indiana""
        },
{
          ""callsign"": ""Russ"",
          ""alias"": ""Russ Fulcher"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Idaho""
        },
{
          ""callsign"": ""Russell"",
          ""alias"": ""Russell Fry"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""South Carolina""
        },
{
          ""callsign"": ""Ryan"",
          ""alias"": ""Ryan Zinke"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Montana""
        },
{
          ""callsign"": ""Salud"",
          ""alias"": ""Salud Carbajal"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""California""
        },
{
          ""callsign"": ""Sam"",
          ""alias"": ""Sam Graves"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Missouri""
        },
{
          ""callsign"": ""Sanford"",
          ""alias"": ""Sanford Bishop Jr."",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Georgia""
        },
{
          ""callsign"": ""Sara"",
          ""alias"": ""Sara Jacobs"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""California""
        },
{
          ""callsign"": ""Scott"",
          ""alias"": ""Scott DesJarlais"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Tennessee""
        },
{
          ""callsign"": ""Scott"",
          ""alias"": ""Scott Fitzgerald"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Wisconsin""
        },
{
          ""callsign"": ""Scott"",
          ""alias"": ""Scott Franklin"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Florida""
        },
{
          ""callsign"": ""Scott"",
          ""alias"": ""Scott Perry"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Pennsylvania""
        },
{
          ""callsign"": ""Scott"",
          ""alias"": ""Scott Peters"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""California""
        },
{
          ""callsign"": ""Sean"",
          ""alias"": ""Sean Casten"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Illinois""
        },
{
          ""callsign"": ""Seth"",
          ""alias"": ""Seth Magaziner"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Rhode Island""
        },
{
          ""callsign"": ""Seth"",
          ""alias"": ""Seth Moulton"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Massachusetts""
        },
{
          ""callsign"": ""Sharice"",
          ""alias"": ""Sharice Davids"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Kansas""
        },
{
          ""callsign"": ""Sheila"",
          ""alias"": ""Sheila Cherfilus-McCormick"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Florida""
        },
{
          ""callsign"": ""Sheila"",
          ""alias"": ""Sheila Jackson Lee"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Texas""
        },
{
          ""callsign"": ""Shontel"",
          ""alias"": ""Shontel Brown"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Ohio""
        },
{
          ""callsign"": ""Shri"",
          ""alias"": ""Shri Thanedar"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Michigan""
        },
{
          ""callsign"": ""Stacey"",
          ""alias"": ""Stacey Plaskett"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Virgin Islands""
        },
{
          ""callsign"": ""Steny"",
          ""alias"": ""Steny Hoyer"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Maryland""
        },
{
          ""callsign"": ""Stephanie"",
          ""alias"": ""Stephanie Bice"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Oklahoma""
        },
{
          ""callsign"": ""Stephen"",
          ""alias"": ""Stephen Lynch"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Massachusetts""
        },
{
          ""callsign"": ""Steve"",
          ""alias"": ""Steve Cohen"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Tennessee""
        },
{
          ""callsign"": ""Steve"",
          ""alias"": ""Steve Scalise"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Louisiana""
        },
{
          ""callsign"": ""Steve"",
          ""alias"": ""Steve Womack"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Arkansas""
        },
{
          ""callsign"": ""Steven"",
          ""alias"": ""Steven Horsford"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Nevada""
        },
{
          ""callsign"": ""Summer"",
          ""alias"": ""Summer Lee"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Pennsylvania""
        },
{
          ""callsign"": ""Susan"",
          ""alias"": ""Susan Wild"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Pennsylvania""
        },
{
          ""callsign"": ""Susie"",
          ""alias"": ""Susie Lee"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Nevada""
        },
{
          ""callsign"": ""Suzan"",
          ""alias"": ""Suzan DelBene"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Washington""
        },
{
          ""callsign"": ""Suzanne"",
          ""alias"": ""Suzanne Bonamici"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Oregon""
        },
{
          ""callsign"": ""Sydney"",
          ""alias"": ""Sydney Kamlager"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""California""
        },
{
          ""callsign"": ""Sylvia"",
          ""alias"": ""Sylvia Garcia"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Texas""
        },
{
          ""callsign"": ""Ted"",
          ""alias"": ""Ted Lieu"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""California""
        },
{
          ""callsign"": ""Teresa"",
          ""alias"": ""Teresa Leger Fernandez"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""New Mexico""
        },
{
          ""callsign"": ""Terri"",
          ""alias"": ""Terri Sewell"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Alabama""
        },
{
          ""callsign"": ""Thomas"",
          ""alias"": ""Thomas Kean Jr."",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""New Jersey""
        },
{
          ""callsign"": ""Thomas"",
          ""alias"": ""Thomas Massie"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Kentucky""
        },
{
          ""callsign"": ""Tim"",
          ""alias"": ""Tim Burchett"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Tennessee""
        },
{
          ""callsign"": ""Tim"",
          ""alias"": ""Tim Walberg"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Michigan""
        },
{
          ""callsign"": ""Tom"",
          ""alias"": ""Tom Cole"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Oklahoma""
        },
{
          ""callsign"": ""Tom"",
          ""alias"": ""Tom Emmer"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Minnesota""
        },
{
          ""callsign"": ""Tom"",
          ""alias"": ""Tom McClintock"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""California""
        },
{
          ""callsign"": ""Tom"",
          ""alias"": ""Tom Tiffany"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Wisconsin""
        },
{
          ""callsign"": ""Tony"",
          ""alias"": ""Tony Cárdenas"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""California""
        },
{
          ""callsign"": ""Tony"",
          ""alias"": ""Tony Gonzales"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Texas""
        },
{
          ""callsign"": ""Tracey"",
          ""alias"": ""Tracey Mann"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Kansas""
        },
{
          ""callsign"": ""Trent"",
          ""alias"": ""Trent Kelly"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Mississippi""
        },
{
          ""callsign"": ""Troy"",
          ""alias"": ""Troy Balderson"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Ohio""
        },
{
          ""callsign"": ""Troy"",
          ""alias"": ""Troy Carter"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Louisiana""
        },
{
          ""callsign"": ""Troy"",
          ""alias"": ""Troy Nehls"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Texas""
        },
{
          ""callsign"": ""Val"",
          ""alias"": ""Val Hoyle"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Oregon""
        },
{
          ""callsign"": ""Valerie"",
          ""alias"": ""Valerie Foushee"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""North Carolina""
        },
{
          ""callsign"": ""Vern"",
          ""alias"": ""Vern Buchanan"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Florida""
        },
{
          ""callsign"": ""Veronica"",
          ""alias"": ""Veronica Escobar"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Texas""
        },
{
          ""callsign"": ""Vicente"",
          ""alias"": ""Vicente Gonzalez Jr."",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Texas""
        },
{
          ""callsign"": ""Victoria"",
          ""alias"": ""Victoria Spartz"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Indiana""
        },
{
          ""callsign"": ""Virginia"",
          ""alias"": ""Virginia Foxx"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""North Carolina""
        },
{
          ""callsign"": ""Warren"",
          ""alias"": ""Warren Davidson"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Ohio""
        },
{
          ""callsign"": ""Wesley"",
          ""alias"": ""Wesley Hunt"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Texas""
        },
{
          ""callsign"": ""Wiley"",
          ""alias"": ""Wiley Nickel"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""North Carolina""
        },
{
          ""callsign"": ""William"",
          ""alias"": ""William Timmons"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""South Carolina""
        },
{
          ""callsign"": ""Yadira"",
          ""alias"": ""Yadira Caraveo"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Colorado""
        },
{
          ""callsign"": ""Young"",
          ""alias"": ""Young Kim"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""California""
        },
{
          ""callsign"": ""Yvette"",
          ""alias"": ""Yvette D. Clarke"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""New York""
        },
{
          ""callsign"": ""Zach"",
          ""alias"": ""Zach Nunn"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""Iowa""
        },
{
          ""callsign"": ""Zoe"",
          ""alias"": ""Zoe Lofgren"",
          ""code"": ""98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892"",
          ""corpro"": """",
          ""frame"": """",
          ""mech"": ""California""
        },





      ],
      "header": {
        "planet": "Legislators.Live",
        "year": "2023",
        "system": "Game of Politics",
        "gate": "Congress",
        "ring": "118th U.S. Congress",
        "headerTitle": "Legislators",
        "headerSubtitle": ".Live",
        "subheaderTitle": "The Lineup",
        "subheaderSubtitle": "118th U.S. Congress",
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
