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
                  <v-form v-model="formValues" class="form-container container">
                    <v-row align="center">
                      <v-checkbox 
                        color="green"
                        v-model="guardian1.new"
                        name="guardian1_new"
                      />
                      <v-text-field 
                      name="guardian1" 
                      v-model="guardian1.name" 
                      placeholder="Guardian 1"
                      clearable
                      />
                    </v-row>
                    <v-row>
                      <v-checkbox
                        color="green"
                        v-model="guardian2.new"
                        name="guardian2_new"
                      />
                      <v-text-field 
                      name="guardian2" 
                      v-model="guardian2.name" 
                      placeholder="Guardian 2"
                      clearable
                      />
                    </v-row>

                    <v-row>
                      <v-checkbox
                        color="green"
                        v-model="guardian3.new"
                        name="guardian3_new"
                      />
                      <v-text-field 
                      name="guardian3"
                      v-model="guardian3.name" 
                      placeholder="Guardian 3" 
                      clearable
                      />
                    </v-row>
                    <v-row>
                      <v-checkbox
                        color="green"
                        v-model="guardian4.new"
                        name="guardian4_new"
                      />
                      <v-text-field 
                      name="guardian4" 
                      v-model="guardian4.name" 
                      placeholder="Guardian 4"
                      clearable
                      />
                    </v-row>
                    <v-row>
                      <v-checkbox
                        color="green"
                        v-model="guardian5.new"
                        name="guardian5_new"
                      />
                      <v-text-field 
                      name="guardian5" 
                      v-model="guardian5.name" 
                      placeholder="Guardian 5"
                      clearable
                      />
                    </v-row>
                    <v-row>
                      <v-checkbox 
                        color="green"
                        v-model="guardian6.new"
                        name="guardian6_new"
                      />
                      <v-text-field 
                      name="guardian6"
                      v-model="guardian6.name" 
                      placeholder="Guardian 6" 
                      clearable
                      />
                    </v-row>
                  </v-form>
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
                      v-model="tab"
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
                      <li><strong :style="guardian1.new ? 'color: red;' : ''">Defender</strong>: {{ guardian1.name }}</li>
                      <li><strong :style="guardian2.new ? 'color: red;' : ''">Runner</strong>: {{ guardian2.name }}</li>
                    </ul>

                    <h2>Team Mid</h2>
                    <ul>
                      <li><strong :style="guardian3.new ? 'color: red;' : ''">Defender</strong>: {{ guardian3.name }}</li>
                      <li><strong :style="guardian4.new ? 'color: red;' : ''">Runner</strong>: {{ guardian4.name }}</li>
                    </ul>

                    <h2>Team Light</h2>
                    <ul>
                      <li><strong :style="guardian5.new ? 'color: red;' : ''">Defender</strong>: {{ guardian5.name }}</li>
                      <li><strong :style="guardian6.new ? 'color: red;' : ''">Runner</strong>: {{ guardian6.name }}</li>
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
                      <li><strong :style="guardian1.new ? 'color: red;' : ''">First</strong>: {{ guardian1.name }}</li>
                      <li><strong :style="guardian2.new ? 'color: red;' : ''">Second</strong>: {{ guardian2.name }}</li>
                    </ul>

                    <h2>Add Clear</h2>
                    <ul>
                      <li :style="guardian3.new ? 'color: red;' : ''">{{ guardian3.name }}</li>
                      <li :style="guardian4.new ? 'color: red;' : ''">{{ guardian4.name }}</li>
                    </ul>

                    <h2>Stunners</h2>
                    <ul>
                      <li :style="guardian5.new ? 'color: red;' : ''">{{ guardian5.name }}</li>
                      <li :style="guardian6.new ? 'color: red;' : ''">{{ guardian6.name }}</li>
                    </ul>
                  </v-card-text>
                </v-card>
              </v-sheet>
              <v-sheet v-show="current === 'Exhibition'">
                <v-card>
                  <v-card-text>
                    <h2>Room 1</h2>
                    <ul>
                      <li><strong :style="guardian1.new ? 'color: red;' : ''">Shard</strong>: {{ guardian1.name }}</li>
                    </ul>

                    <h2>Room 2</h2>
                    <ul>
                      <li><strong :style="guardian2.new ? 'color: red;' : ''">Shard</strong>: {{ guardian2.name }}</li>
                      <li><strong :style="guardian3.new ? 'color: red;' : ''">Relic</strong>: {{ guardian3.name }}</li>
                    </ul>

                    <h2>Room 3</h2>
                    <ul>
                      <li><strong :style="guardian4.new ? 'color: red;' : ''">Shard</strong>: {{ guardian4.name }}</li>
                      <li><strong :style="guardian5.new ? 'color: red;' : ''">Relic</strong>: {{ guardian5.name }}</li>
                      <li><strong :style="guardian6.new ? 'color: red;' : ''">Blight</strong>: {{ guardian6.name }}</li>
                    </ul>
                      
                    <h2>Room 4</h2>
                    <ul>
                      <li><strong :style="guardian2.new ? 'color: red;' : ''">Shard</strong>: {{ guardian2.name }}</li>
                      <li><strong :style="guardian3.new ? 'color: red;' : ''">Relic</strong>: {{ guardian3.name }}</li>
                      <li><strong :style="guardian1.new ? 'color: red;' : ''">Blight</strong>: {{ guardian1.name }}</li>
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
                      <li><strong :style="guardian1.new ? 'color: red;' : ''">First</strong>: {{ guardian1.name }}</li>
                      <li><strong :style="guardian2.new ? 'color: red;' : ''">Second</strong>: {{ guardian2.name }}</li>
                    </ul>

                    <h2>Passers</h2>
                    <ul>
                      <li><strong :style="guardian3.new ? 'color: red;' : ''">First</strong>: {{ guardian3.name }}</li>
                      <li><strong :style="guardian4.new ? 'color: red;' : ''">Second</strong>: {{ guardian4.name }}</li>
                    </ul>

                    <h2>Adds / Callouts</h2>
                    <ul>
                      <li><strong :style="guardian5.new ? 'color: red;' : ''">Left</strong>: {{ guardian5.name }}</li>
                      <li><strong :style="guardian6.new ? 'color: red;' : ''">Right</strong>: {{ guardian6.name }}</li>
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
      guardian1: {
        name: '',
        new: false
      },
      guardian2: {
        name: '',
        new: false
      },
      guardian3: {
        name: '',
        new: false
      },
      guardian4: {
        name: '',
        new: false
      },
      guardian5: {
        name: '',
        new: false
      },
      guardian6: {
        name: '',
        new: false
      },
    }),
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
  color: red;
}

.encounter-map {
  margin: 2rem 0 0;
}

.encounter-map + .v-image {
  margin-top: 2rem;
}
</style>