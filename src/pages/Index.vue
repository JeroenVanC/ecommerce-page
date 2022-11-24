<script setup lang="ts">
import L from 'leaflet'
import 'leaflet/dist/leaflet.css'
import type { Icon, Map, Marker, TileLayer } from 'leaflet'
import { ref } from 'vue'
import ZoomInIcon from '../components/icons/ZoomInIcon.vue'
import ZoonOutIcon from '../components/icons/ZoonOutIcon.vue'
import { useMapIcons } from '../composables/mapIcons.composable'

const mapDiv = ref<Map>()

const { mapConesIcon } = useMapIcons()

const zoomIn = () => {
  mapDiv.value?.setZoom(mapDiv.value.getZoom() + 1)
}

const zoomOut = () => {
  mapDiv.value?.setZoom(mapDiv.value.getZoom() - 1)
}

onMounted(() => {
  mapDiv.value = L.map('mapContainer', { zoomControl: false }).setView([50.8732, 5.5184], 13)
  L.tileLayer(
    'https://tile.openstreetmap.org/{z}/{x}/{y}.png',
    {
      maxZoom: 19,
      attribution: '&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a>',
    }).addTo(mapDiv.value)

  L.marker([50.8732, 5.5184], {
    icon: mapConesIcon,
  }).addTo(mapDiv.value)

  L.marker([50.86, 5.5284], {
    icon: mapConesIcon,
  }).addTo(mapDiv.value)
})
</script>

<template>
  <div id="container" class="flex justify-center items-center mt-20">
    <div class="relative border-8 border-yellow-500">
      <div id="mapContainer" class="w-[80vw] h-[40vh]  bg-red-500" />

      <div class="absolute bottom-0 right-0 z-999 flex flex-col m-4 mb-7 scale-[1.3]">
        <div class="" @click="zoomIn">
          <ZoomInIcon />
        </div>
        <div class="" @click="zoomOut">
          <ZoonOutIcon />
        </div>
      </div>
    </div>
  </div>
</template>
