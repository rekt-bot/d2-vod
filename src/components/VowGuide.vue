<template>
  <v-app id="vow-guide">
    <v-main class="grey lighten-3">
      <v-container>
        <v-row>
          <v-col
            cols="12"
            sm="12"
            lg="4"
          >
            <v-expansion-panels accordion>
              <v-expansion-panel>
                <v-expansion-panel-header>Fireteam</v-expansion-panel-header>
                <v-expansion-panel-content>
                  <v-row>
                  <v-form class="form-container container">
                    <v-row align="center">
                      <v-checkbox 
                        color="green"
                        v-model="guardians[0].new"
                        name="guardian1_new"
                      />
                      <v-text-field 
                      name="guardian1" 
                      v-model="guardians[0].name" 
                      placeholder="Guardian 1"
                      clearable
                      />
                    </v-row>
                    <v-row>
                      <v-checkbox
                        color="green"
                        v-model="guardians[1].new"
                        name="guardian2_new"
                      />
                      <v-text-field 
                      name="guardian2" 
                      v-model="guardians[1].name" 
                      placeholder="Guardian 2"
                      clearable
                      />
                    </v-row>

                    <v-row>
                      <v-checkbox
                        color="green"
                        v-model="guardians[2].new"
                        name="guardian3_new"
                      />
                      <v-text-field 
                      name="guardian3"
                      v-model="guardians[2].name" 
                      placeholder="Guardian 3" 
                      clearable
                      />
                    </v-row>
                    <v-row>
                      <v-checkbox
                        color="green"
                        v-model="guardians[3].new"
                        name="guardian4_new"
                      />
                      <v-text-field 
                      name="guardian4" 
                      v-model="guardians[3].name" 
                      placeholder="Guardian 4"
                      clearable
                      />
                    </v-row>
                    <v-row>
                      <v-checkbox
                        color="green"
                        v-model="guardians[4].new"
                        name="guardian5_new"
                      />
                      <v-text-field 
                      name="guardian5" 
                      v-model="guardians[4].name" 
                      placeholder="Guardian 5"
                      clearable
                      />
                    </v-row>
                    <v-row>
                      <v-checkbox 
                        color="green"
                        v-model="guardians[5].new"
                        name="guardian6_new"
                      />
                      <v-text-field 
                      name="guardian6"
                      v-model="guardians[5].name" 
                      placeholder="Guardian 6" 
                      clearable
                      />
                    </v-row>
                  </v-form>
                  <v-btn
                      elevation="2"
                      class="randomize-fireteam"
                      @click="randomizeFireteam"
                    >Randomize Fireteam</v-btn>
                  </v-row>
                </v-expansion-panel-content>
              </v-expansion-panel>
            </v-expansion-panels>
          </v-col>

          <v-col
            cols="12"
            sm="12"
            lg="8"
          >
              <v-card>
                <v-toolbar
                  color="#333"
                  dark
                  flat
                >
                  <template>
                    <v-tabs
                      align-with-title
                    >
                      <v-tabs-slider color="red"></v-tabs-slider>

                      <v-tab
                        v-for="encounter in encounters"
                        :key="encounter.name"
                        @click="current.name = encounter.name"
                      >
                        {{ encounter.name }}
                      </v-tab>
                    </v-tabs>
                  </template>
                </v-toolbar>
              </v-card>
              <v-sheet v-show="current.name === 'Acquisition'">
                <v-card>
                  <v-card-text>
                    <h2>Team Dark</h2>
                    <ul>
                      <li><strong :style="guardians[0].new ? 'color: green;' : ''">Defender</strong>: {{ guardians[0].name }}</li>
                      <li><strong :style="guardians[1].new ? 'color: green;' : ''">Runner</strong>: {{ guardians[1].name }}</li>
                    </ul>

                    <h2>Team Mid</h2>
                    <ul>
                      <li><strong :style="guardians[2].new ? 'color: green;' : ''">Defender</strong>: {{ guardians[2].name }}</li>
                      <li><strong :style="guardians[3].new ? 'color: green;' : ''">Runner</strong>: {{ guardians[3].name }}</li>
                    </ul>

                    <h2>Team Light</h2>
                    <ul>
                      <li><strong :style="guardians[4].new ? 'color: green;' : ''">Defender</strong>: {{ guardians[4].name }}</li>
                      <li><strong :style="guardians[5].new ? 'color: green;' : ''">Runner</strong>: {{ guardians[5].name }}</li>
                    </ul>
                    <div class="encounter-extras">
                      <v-btn
                        elevation="2"
                        class="encounter-challenge"
                        @click="encounters[0].challenge = !encounters[0].challenge"
                      >Loot Challenge</v-btn>
                      <v-btn
                        elevation="2"
                        class="encounter-triumph"
                        @click="encounters[0].triumph = !encounters[0].triumph"
                      >Title Triumph</v-btn>
                      <v-btn
                        elevation="2"
                        class="encounter-map"
                        @click="encounters[0].graphic = !encounters[0].graphic"
                      >Graphic</v-btn>
                      <v-card-text v-if="encounters[0].challenge">
                        <h3>Extra Loot Challenge</h3>
                        <p><strong>Swift Destruction</strong> - All three Unstoppable Ogres must be killed at the same time, each round. Killing a Glyph Keeper spawns an ogre.</p>
                      </v-card-text>
                      <v-card-text v-if="encounters[0].triumph">
                        <h3>Title Triumph</h3>
                        <p><strong>On My Go</strong> - Cannot kill Abated Adherent enemies until they attack your obelisk.</p>
                      </v-card-text>
                      <v-card-text
                          v-if="encounters[0].graphic"
                        >
                        <v-img
                          max-width="100%"
                          src="https://i.imgur.com/JlCqk9e.png" />
                      </v-card-text>
                    </div>
                  </v-card-text>
                </v-card>
              </v-sheet>
              <v-sheet v-show="current.name === 'Collection'">
                <v-card>
                  <v-card-text>
                    <h2>Totem Team</h2>
                    <ul>
                      <li><strong :style="guardians[0].new ? 'color: green;' : ''">First</strong>: {{ guardians[0].name }}</li>
                      <li><strong :style="guardians[1].new ? 'color: green;' : ''">Second</strong>: {{ guardians[1].name }}</li>
                    </ul>

                    <h2>Add Clear</h2>
                    <ul>
                      <li :style="guardians[2].new ? 'color: green;' : ''">{{ guardians[2].name }}</li>
                      <li :style="guardians[3].new ? 'color: green;' : ''">{{ guardians[3].name }}</li>
                    </ul>

                    <h2>Stunners</h2>
                    <ul>
                      <li :style="guardians[4].new ? 'color: green;' : ''">{{ guardians[4].name }}</li>
                      <li :style="guardians[5].new ? 'color: green;' : ''">{{ guardians[5].name }}</li>
                    </ul>
                    <div class="encounter-extras">
                      <v-btn
                        elevation="2"
                        class="encounter-triumph"
                        @click="encounters[1].triumph = !encounters[1].triumph"
                      >Title Triumph</v-btn>
                      <v-card-text v-if="encounters[1].triumph">
                        <h3>Title Triumph</h3>
                        <p><strong>Handle With Care</strong> - Defeat The Caretaker while having every member of your fireteam stun at least once per floor.</p>
                      </v-card-text>
                    </div>
                  </v-card-text>
                </v-card>
              </v-sheet>
              <v-sheet v-show="current.name === 'Exhibition'">
                <v-card>
                  <v-card-text>
                    <h2>Room 1</h2>
                    <ul>
                      <li><strong :style="guardians[0].new ? 'color: green;' : ''"><v-icon color="#35c2f7">mdi-star</v-icon>Shard</strong>: {{ guardians[0].name }}</li>
                    </ul>

                    <h2>Room 2</h2>
                    <ul>
                      <li><strong :style="guardians[1].new ? 'color: green;' : ''"><v-icon color="#35c2f7">mdi-star</v-icon>Shard</strong>: {{ guardians[1].name }}</li>
                      <li><strong :style="guardians[2].new ? 'color: green;' : ''"><v-icon>mdi-baseball-diamond</v-icon>Relic</strong>: {{ guardians[2].name }}</li>
                    </ul>

                    <h2>Room 3</h2>
                    <ul>
                      <li><strong :style="guardians[3].new ? 'color: green;' : ''"><v-icon color="#35c2f7">mdi-star</v-icon>Shard</strong>: {{ guardians[3].name }}</li>
                      <li><strong :style="guardians[4].new ? 'color: green;' : ''"><v-icon>mdi-baseball-diamond</v-icon>Relic</strong>: {{ guardians[4].name }}</li>
                      <li><strong :style="guardians[5].new ? 'color: green;' : ''"><v-icon color="#205300">mdi-biohazard</v-icon>Blight</strong>: {{ guardians[5].name }}</li>
                    </ul>
                      
                    <h2>Room 4</h2>
                    <ul>
                      <li><strong :style="guardians[1].new ? 'color: green;' : ''"><v-icon color="#35c2f7">mdi-star</v-icon>Shard</strong>: {{ guardians[1].name }}</li>
                      <li><strong :style="guardians[2].new ? 'color: green;' : ''"><v-icon>mdi-baseball-diamond</v-icon>Relic</strong>: {{ guardians[2].name }}</li>
                      <li><strong :style="guardians[0].new ? 'color: green;' : ''"><v-icon color="#205300">mdi-biohazard</v-icon>Blight</strong>: {{ guardians[0].name }}</li>
                    </ul>
                    <div class="encounter-extras">
                      <v-btn
                        elevation="2"
                        class="encounter-triumph"
                        @click="encounters[2].triumph = !encounters[2].triumph"
                      >Title Triumph</v-btn>
                      <v-btn
                        elevation="2"
                        class="encounter-map"
                        @click="encounters[2].graphic = !encounters[2].graphic"
                      >Graphic</v-btn>
                      <v-card-text v-if="encounters[2].triumph">
                        <h3>Title Triumph</h3>
                        <p><strong>Glyph to Glyph</strong> - Kill each set of Glyphkeepers in Exhibition within 5 seconds of each other.</p>
                      </v-card-text>
                      <v-card-text
                          v-if="encounters[2].graphic"
                        >
                        <v-img
                          max-width="100%"
                          src="https://i.imgur.com/2mDtrov.png" />
                      </v-card-text>
                    </div>
                  </v-card-text>
                </v-card>
              </v-sheet>
              <v-sheet v-show="current.name === 'Dominion'">
                <v-card>
                  <v-card-text>
                    <h2>Dunkers (Both Phases)</h2>
                    <ul>
                      <li><strong :style="guardians[0].new ? 'color: green;' : ''">First</strong>: {{ guardians[0].name }}</li>
                      <li><strong :style="guardians[1].new ? 'color: green;' : ''">Second</strong>: {{ guardians[1].name }}</li>
                    </ul>

                    <h2>Passers</h2>
                    <ul>
                      <li><strong :style="guardians[2].new ? 'color: green;' : ''">First</strong>: {{ guardians[2].name }}</li>
                      <li><strong :style="guardians[3].new ? 'color: green;' : ''">Second</strong>: {{ guardians[3].name }}</li>
                    </ul>

                    <h2>Adds / Callouts</h2>
                    <ul>
                      <li><strong :style="guardians[4].new ? 'color: green;' : ''">Left</strong>: {{ guardians[4].name }}</li>
                      <li><strong :style="guardians[5].new ? 'color: green;' : ''">Right</strong>: {{ guardians[5].name }}</li>
                    </ul>
                    <div class="encounter-extras">
                      <v-btn
                        elevation="2"
                        class="encounter-triumph"
                        @click="encounters[3].triumph = !encounters[3].triumph"
                      >Title Triumph</v-btn>
                      <v-btn
                        elevation="3"
                        class="encounter-map"
                        @click="encounters[3].graphic = !encounters[3].graphic"
                      >Graphic</v-btn>
                      <v-card-text v-if="encounters[3].triumph">
                        <h3>Title Triumph</h3>
                        <p><strong>Symmetrical Energy</strong> - Any energy deposit in Dominion must be accompanied by another deposit within 5 seconds.</p>
                      </v-card-text>
                      <v-card-text
                          v-if="encounters[3].graphic"
                        >
                        <v-img
                          max-width="100%"
                          src="https://i.imgur.com/XoJA8em.png" />
                      </v-card-text>
                    </div>
                  </v-card-text>
                </v-card>
              </v-sheet>
              <v-sheet v-show="current.name === 'Extra'">
                <v-card>
                  <v-card-text>
                    <h2>Extra Loot Chest</h2>
                    <v-sheet class="vow-extra toggles">
                      <v-btn outlined @click="extraToggle">Pyramid</v-btn>
                      <v-btn outlined @click="extraToggle">Hands</v-btn>
                      <v-btn outlined @click="extraToggle">Darkness</v-btn>
                      <v-btn outlined @click="extraToggle">Traveller</v-btn>
                      <v-btn outlined @click="extraToggle">Praise</v-btn>
                      <v-btn outlined @click="extraToggle">Light</v-btn>
                      <v-btn outlined @click="extraToggle">Square</v-btn>
                      <v-btn outlined @click="extraToggle">T-Pose</v-btn>
                      <v-btn outlined @click="extraToggle">Kill</v-btn>
                    </v-sheet>
                    
                    <v-sheet class="location pyramid" v-if="this.extraSymbols.pyramid">
                      <h2>Pyramid Symbol Location</h2>
                      <p>Just after starting symbol drop-down</p>
                      <v-img src="https://i.imgur.com/UEWgMZJ.jpeg" />
                    </v-sheet>

                    <v-sheet class="location hands" v-if="this.extraSymbols.hands">
                      <h2>Hands Symbol Location</h2>
                      <p>Just before first encounter</p>
                      <v-img src="https://i.imgur.com/d8frflt.jpeg" />
                    </v-sheet>

                    <v-sheet class="location darkness" v-if="this.extraSymbols.darkness">
                      <h2>Darkness Symbol Location</h2>
                      <p>Left side of Totem encounter room</p>
                      <v-img src="https://i.imgur.com/JezBnpZ.jpeg" />
                    </v-sheet>

                    <v-sheet class="location traveller" v-if="this.extraSymbols.traveller">
                      <h2>Traveller Symbol Location</h2>
                      <p>A couple of rooms after the many-assed horse</p>
                      <v-img src="https://i.imgur.com/avPwxY2.jpeg" />
                    </v-sheet>
                    
                    <v-sheet class="location praise" v-if="this.extraSymbols.praise">
                      <h2>Praise Symbol Location</h2>
                      <p>After the Gatekeeper encounter</p>
                      <v-img src="https://i.imgur.com/xzpEw1b.jpeg" />
                    </v-sheet>
                    
                    <v-sheet class="location light" v-if="this.extraSymbols.light">
                      <h2>Light Symbol Location</h2>
                      <p>During the jumping puzzle section</p>
                      <v-img src="https://i.imgur.com/3NkI1am.jpeg" />
                    </v-sheet>
                    
                    <v-sheet class="location square" v-if="this.extraSymbols.square">
                      <h2>Square Symbol Location</h2>
                      <p>Further along same jumping puzzle</p>
                      <v-img src="https://i.imgur.com/KGXEoEp.jpeg" />
                    </v-sheet>
                    
                    <v-sheet class="location tpose" v-if="this.extraSymbols.tpose">
                      <h2>T-Pose Symbol Location</h2>
                      <p>After relic encounter, up left stairs</p>
                      <v-img src="https://i.imgur.com/qyFKq9h.jpeg" />
                    </v-sheet>
                    
                    <v-sheet class="location kill" v-if="this.extraSymbols.kill">
                      <h2>Kill Symbol Location</h2>
                      <p>Final platforming area before boss arena</p>
                      <v-img src="https://i.imgur.com/ooI98WP.jpeg" />
                    </v-sheet>
                  </v-card-text>
                </v-card>
              </v-sheet>
          </v-col>
        </v-row>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
  export default {
    name: 'VowGuide',
    data: () => ({
      encounters: [
        {
          name: 'Acquisition',
          graphic: false,
          challenge: false,
          triumph: false,
        },
        {
          name: 'Collection',
          graphic: false,
          challenge: false,
          triumph: false,
        },
        {
          name: 'Exhibition',
          graphic: false,
          challenge: false,
          triumph: false,
        },
        {
          name: 'Dominion',
          graphic: false,
          challenge: false,
          triumph: false,
        },
        {
          name: 'Extra',
          graphic: false,
          challenge: false,
          triumph: false,
        },
      ],
      current: {
        name: 'Acquisition',
      },
      guardians: [
        {
          name: '',
          new: false
        },
        {
          name: '',
          new: false
        },
        {
          name: '',
          new: false
        },
        {
          name: '',
          new: false
        },
        {
          name: '',
          new: false
        },
        {
          name: '',
          new: false
        },
      ],
      extraSymbols: {
        active: 0,
        pyramid: false,
        hands: false,
        darkness: false,
        traveller: false,
        praise: false,
        light: false,
        square: false,
        tpose: false,
        kill: false
      },
    }),
    methods: {
      randomizeFireteam: function() {
        let currentFireteam = this.guardians;
        let m = 0;

        for (let i = currentFireteam.length - 1; i > 0; i--) {
          const j = Math.floor(Math.random() * (i + 1));
          [currentFireteam[i], currentFireteam[j]] = [currentFireteam[j], currentFireteam[i]];
        }
        
        currentFireteam.forEach(member => {
          this.guardians[m].name = member.name;
          this.guardians[m].new = member.new;
          m++;
        })

        this.$forceUpdate();
      },

      extraToggle: function(e) {
        e.currentTarget.classList.toggle('v-item--active');
        let secretSymbol = e.target.innerHTML.toLowerCase().replaceAll(/-| /g,'');
        this.extraSymbols[secretSymbol] = !this.extraSymbols[secretSymbol];
      },
    }
  }
</script>

<style>

ul {
  padding-left: 0;
}

ul + h2 {
  margin-top: 2rem;
}

li {
  list-style-type: none;
  padding-left: 0;
}

.sherpa {
  color: green;
}

.encounter-map + .v-image {
  margin-top: 2rem;
}

.randomize-fireteam {
  margin: 1rem;
}

.vow-extra {
  display: flex;
  justify-content: space-evenly;
  margin: 2rem 0;
  flex-wrap: wrap;
}

.vow-extra.toggles {
  margin-bottom: 2rem;
}

.toggles button {
  margin-bottom: 0.5rem;
}

.theme--light.v-item--active {
  background: #333;
}

.theme--light.v-item--active .v-btn__content {
  color: white;
}

.location + .location {
  margin-top: 2rem;
}

.encounter-extras {
  margin-top: 2rem;
}

.encounter-extras button {
  margin-right: 1rem;
}
</style>