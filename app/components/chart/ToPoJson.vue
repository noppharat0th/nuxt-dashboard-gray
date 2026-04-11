<script setup lang="ts">
import { WorldMapTopoJSON } from "@unovis/ts/maps";
import { geoMercator } from "d3-geo";

const worldData = computed(() => ({
  areas: [
    { id: "NL", count: 94, name: "Netherlands" },
    { id: "US", count: 91, name: "United States" },
    { id: "DE", count: 71, name: "Germany" },
    { id: "BR", count: 60, name: "Brazil" },
    { id: "FR", count: 59, name: "France" },
    { id: "ID", count: 48, name: "Indonesia" },
    { id: "KE", count: 42, name: "Kenya" },
    { id: "GB", count: 35, name: "United Kingdom" },
    { id: "CA", count: 30, name: "Canada" },
  ],
  points: [
    { id: "ams", latitude: 52.3676, longitude: 4.9041, label: "Amsterdam" },
  ],
  links: [
    { source: "ams", target: "nyc" },
    { source: "tyo", target: "ams" },
  ],
}));

const customProjection = geoMercator().center([0, 0]);
</script>

<template>
  <div class="py-6">
    <TopoJSONMap
      :height="400"
      map-feature-key="countries"
      :projection="customProjection"
      :data="worldData"
      :topo-json="WorldMapTopoJSON"
      :zoom-factor="1.1"
    />
  </div>
</template>