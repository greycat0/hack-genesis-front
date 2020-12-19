<template>
  <div class="d-flex">
    <russian-map
      class="flex-grow-1"
      :pickedRegions="pickedRegions"
      @add="(regionID) => this.pickedRegions.push(regionID)"
      @delete="
        (regionID) =>
          (pickedRegions = pickedRegions.filter((r) => r != regionID))
      "
    />
    <v-card style="max-width: 300px">
      <v-toolbar flat color="deep-purple accent-4" dark>
        <v-toolbar-title>Фильтры</v-toolbar-title>
      </v-toolbar>
      <v-card-text>
        <h2 class="title mb-2">Регионы</h2>

        <v-chip-group column multiple>
          <v-chip v-for="region in pickedRegions" :key="region" outlined>
            {{ regions[region] }}
          </v-chip>
        </v-chip-group>
      </v-card-text>

      <v-card-text>
        <h2 class="title mb-2">Период</h2>

        <v-date-picker v-model="dates" range></v-date-picker>
      </v-card-text>
    </v-card>
  </div>
</template>

<script>
import Map from '~/components/Map'
import { regions } from '~/components/regions'
export default {
  components: {
    RussianMap: Map,
  },
  data() {
    return {
      dates: [],
      regions,
      pickedRegions: [],
    }
  },
}
</script>

<style>
</style>