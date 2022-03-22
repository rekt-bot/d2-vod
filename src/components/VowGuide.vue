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
            <v-sheet
              rounded="lg"
              min-height="268"
            >
              <v-card>
                <v-card-text>
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
                </v-card-text>
              </v-card>
            </v-sheet>
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
                        v-for="link in links"
                        :key="link"
                        @click="current = link"
                      >
                        {{ link }}
                      </v-tab>
                    </v-tabs>
                  </template>
                </v-toolbar>
              </v-card>
              <v-sheet v-show="current === 'Acquisition'">
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
                    <v-btn
                      elevation="2"
                      class="encounter-map"
                      @click="showAcquisitionMap = !showAcquisitionMap"
                    >Show Graphic</v-btn>
                    <v-img
                      v-if="showAcquisitionMap"
                      max-width="100%"
                      src="https://i.imgur.com/JlCqk9e.png" />
                  </v-card-text>
                </v-card>
              </v-sheet>
              <v-sheet v-show="current === 'Collection'">
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
                  </v-card-text>
                </v-card>
              </v-sheet>
              <v-sheet v-show="current === 'Exhibition'">
                <v-card>
                  <v-card-text>
                    <h2>Room 1</h2>
                    <ul>
                      <li><strong :style="guardians[0].new ? 'color: green;' : ''">Shard</strong>: {{ guardians[0].name }}</li>
                    </ul>

                    <h2>Room 2</h2>
                    <ul>
                      <li><strong :style="guardians[1].new ? 'color: green;' : ''">Shard</strong>: {{ guardians[1].name }}</li>
                      <li><strong :style="guardians[2].new ? 'color: green;' : ''">Relic</strong>: {{ guardians[2].name }}</li>
                    </ul>

                    <h2>Room 3</h2>
                    <ul>
                      <li><strong :style="guardians[3].new ? 'color: green;' : ''">Shard</strong>: {{ guardians[3].name }}</li>
                      <li><strong :style="guardians[4].new ? 'color: green;' : ''">Relic</strong>: {{ guardians[4].name }}</li>
                      <li><strong :style="guardians[5].new ? 'color: green;' : ''">Blight</strong>: {{ guardians[5].name }}</li>
                    </ul>
                      
                    <h2>Room 4</h2>
                    <ul>
                      <li><strong :style="guardians[1].new ? 'color: green;' : ''">Shard</strong>: {{ guardians[1].name }}</li>
                      <li><strong :style="guardians[2].new ? 'color: green;' : ''">Relic</strong>: {{ guardians[2].name }}</li>
                      <li><strong :style="guardians[0].new ? 'color: green;' : ''">Blight</strong>: {{ guardians[0].name }}</li>
                    </ul>
                    <v-btn
                      elevation="2"
                      class="encounter-map"
                      @click="showExhibitionMap = !showExhibitionMap"
                    >Show Graphic</v-btn>
                    <v-img
                      v-if="showExhibitionMap"
                      max-width="100%"
                      src="https://i.imgur.com/2mDtrov.png" />
                  </v-card-text>
                </v-card>
              </v-sheet>
              <v-sheet v-show="current === 'Dominion'">
                <v-card>
                  <v-card-text>
                    <h2>Dunkers</h2>
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
                    <v-btn
                      elevation="2"
                      class="encounter-map"
                      @click="showDominionMap = !showDominionMap"
                    >Show Graphic</v-btn>
                    <v-img
                      v-if="showDominionMap"
                      max-width="100%"
                      src="https://i.imgur.com/XoJA8em.png" />
                  </v-card-text>
                </v-card>
              </v-sheet>
              <v-sheet v-show="current === 'Extras'">
                <v-card>
                  <v-card-text>
                    <h2>Extra Loot Chest</h2>

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
      links: [
        'Acquisition',
        'Collection',
        'Exhibition',
        'Dominion',
        'Extra',
      ],
      current: 'Acquisition',
      showAcquisitionMap: false,
      showExhibitionMap: false,
      showDominionMap: false,
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
    }
  }
</script>

<style scoped>

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

.encounter-map {
  margin: 2rem 0 0;
}

.encounter-map + .v-image {
  margin-top: 2rem;
}

.randomize-fireteam {
  margin: 1rem;
}
</style>