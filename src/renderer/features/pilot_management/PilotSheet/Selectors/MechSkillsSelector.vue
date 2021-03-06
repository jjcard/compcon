<template>
  <v-container style="overflow-y: scroll">
    <v-layout align-center justify-center column>
      <v-alert value="true" :type="pilot.IsMissingHASE ? 'info' : 'success'" outline>
        {{ pilot.CurrentHASEPoints }}/{{ pilot.MaxHASEPoints }} Mech Skills selected
      </v-alert>
    </v-layout>
    <v-layout align-center justify-center column>
      <v-flex><span class="headline">HULL</span></v-flex>
      <v-flex>
        <span class="font-weight-light">
          Your HULL skill describes your ability to build and pilot durable, heavy mechs that can
          take punches and keep going
        </span>
      </v-flex>
      <v-flex>
        <v-btn icon left bottom @click="remove('Hull')">
          <v-icon>remove</v-icon>
        </v-btn>
        <v-rating
          class="d-inline-block"
          v-model="pilot.MechSkills.Hull"
          hover
          x-large
          length="6"
          readonly
          empty-icon="mdi-hexagon-outline"
          full-icon="mdi-hexagon-slice-6"
        />
        <v-btn :disabled="!pilot.IsMissingHASE" icon right bottom @click="add('Hull')">
          <v-icon>add</v-icon>
        </v-btn>
      </v-flex>
    </v-layout>
    <v-layout class="bonus-text" justify-center row>
      <v-flex shrink>
        <span class="minor-title">MECH HP</span>
        <span class="minor-title primary--text">+{{ pilot.MechSkills.Hull * 2 }}</span>
      </v-flex>
      <v-flex shrink class="ml-2 mr-2">
        <span class="fluff-text grey--text">//</span>
      </v-flex>
      <v-flex shrink>
        <span class="minor-title">REPAIR CAPACITY</span>
        <span class="minor-title primary--text">+{{ Math.floor(pilot.MechSkills.Hull / 2) }}</span>
      </v-flex>
    </v-layout>
    <v-divider class="ml-2 mr-2 mt-0 pt-0 mb-3" />
    <v-layout align-center justify-center column>
      <v-flex><span class="headline">AGILITY</span></v-flex>
      <v-flex>
        <span class="font-weight-light">
          Your AGILITY skill describes your ability to build and pilot fast, evasive mechs
        </span>
      </v-flex>
      <v-flex>
        <v-btn icon left bottom @click="remove('Agi')">
          <v-icon>remove</v-icon>
        </v-btn>
        <v-rating
          class="d-inline-block"
          v-model="pilot.MechSkills.Agi"
          hover
          x-large
          length="6"
          readonly
          empty-icon="mdi-hexagon-outline"
          full-icon="mdi-hexagon-slice-6"
        />
        <v-btn :disabled="!pilot.IsMissingHASE" icon right bottom @click="add('Agi')">
          <v-icon>add</v-icon>
        </v-btn>
      </v-flex>
      <v-layout class="bonus-text" justify-center row>
        <v-flex shrink>
          <span class="minor-title">EVASION</span>
          <span class="minor-title primary--text">+{{ pilot.MechSkills.Agi }}</span>
        </v-flex>
        <v-flex shrink class="ml-2 mr-2">
          <span class="fluff-text grey--text">//</span>
        </v-flex>
        <v-flex shrink>
          <span class="minor-title">SPEED</span>
          <span class="minor-title primary--text">+{{ Math.floor(pilot.MechSkills.Agi / 2) }}</span>
        </v-flex>
      </v-layout>
    </v-layout>
    <v-divider class="ml-2 mr-2 mt-0 pt-0 mb-3" />
    <v-layout align-center justify-center column>
      <v-flex><span class="headline">SYSTEMS</span></v-flex>
      <v-flex>
        <span class="font-weight-light">
          Your SYSTEMS skill describes your ability to build and pilot technical mechs with powerful
          electronic warfare tools
        </span>
      </v-flex>
      <v-flex>
        <v-btn icon left bottom @click="remove('Sys')">
          <v-icon>remove</v-icon>
        </v-btn>
        <v-rating
          class="d-inline-block"
          v-model="pilot.MechSkills.Sys"
          hover
          x-large
          length="6"
          readonly
          empty-icon="mdi-hexagon-outline"
          full-icon="mdi-hexagon-slice-6"
        />
        <v-btn :disabled="!pilot.IsMissingHASE" icon right bottom @click="add('Sys')">
          <v-icon>add</v-icon>
        </v-btn>
      </v-flex>
    </v-layout>
    <v-layout class="bonus-text" justify-center row>
      <v-flex shrink>
        <span class="minor-title">ELECTRONIC DEFENSE</span>
        <span class="minor-title primary--text">+{{ pilot.MechSkills.Sys }}</span>
      </v-flex>
      <v-flex shrink class="ml-2 mr-2">
        <span class="fluff-text grey--text">//</span>
      </v-flex>
      <v-flex shrink>
        <span class="minor-title">TECH ATTACK</span>
        <span class="minor-title primary--text">+{{ pilot.MechSkills.Sys }}</span>
      </v-flex>
      <v-flex shrink class="ml-2 mr-2">
        <span class="fluff-text grey--text">//</span>
      </v-flex>
      <v-flex shrink>
        <span class="minor-title">SP</span>
        <span class="minor-title primary--text">+{{ Math.floor(pilot.MechSkills.Sys / 2) }}</span>
      </v-flex>
    </v-layout>
    <v-divider class="ml-2 mr-2 mt-0 pt-0 mb-3" />
    <v-layout align-center justify-center column>
      <v-flex><span class="headline">ENGINEERING</span></v-flex>
      <v-flex>
        <span class="font-weight-light">
          Your ENGINEERING skill describes your ability to build and pilot mechs with powerful
          reactors, supplies and support systems
        </span>
      </v-flex>
      <v-flex>
        <v-btn icon left bottom @click="remove('Eng')">
          <v-icon>remove</v-icon>
        </v-btn>
        <v-rating
          class="d-inline-block"
          v-model="pilot.MechSkills.Eng"
          hover
          x-large
          length="6"
          readonly
          empty-icon="mdi-hexagon-outline"
          full-icon="mdi-hexagon-slice-6"
        />
        <v-btn :disabled="!pilot.IsMissingHASE" icon right bottom @click="add('Eng')">
          <v-icon>add</v-icon>
        </v-btn>
      </v-flex>
    </v-layout>
    <v-layout class="bonus-text" justify-center row>
      <v-flex shrink>
        <span class="minor-title">HEAT CAPACITY</span>
        <span class="minor-title primary--text">+{{ pilot.MechSkills.Eng }}</span>
      </v-flex>
      <v-flex shrink class="ml-2 mr-2">
        <span class="fluff-text grey--text">//</span>
      </v-flex>
      <v-flex shrink>
        <span class="minor-title">LIMITED SYSTEMS BONUS</span>
        <span class="minor-title primary--text">+{{ Math.floor(pilot.MechSkills.Eng / 2) }}</span>
      </v-flex>
    </v-layout>
  </v-container>
</template>

<script lang="ts">
import Vue from 'vue'
import { Pilot, HASE } from '@/class'

export default Vue.extend({
  name: 'mech-skills-selector',
  props: {
    pilot: Pilot,
  },
  methods: {
    add(field: HASE) {
      this.pilot.MechSkills.Increment(field)
    },
    remove(field: HASE) {
      this.pilot.MechSkills.Decrement(field)
    },
    close() {
      this.$emit('close')
    },
  },
})
</script>

<style scoped>
.bonus-text {
  position: relative;
  bottom: 20px;
}
</style>
