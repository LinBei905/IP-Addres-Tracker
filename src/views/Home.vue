<template>
  <div class="flex flex-col h-screen max-h-screen">
    <!-- nav -->
    <div
      class="flex justify-center relative bg-hero-pattern bg-cover px-4 pt-8 pb-32 z-20"
    >
      <!-- input -->
      <div class="w-full max-w-screen-sm">
        <h1 class="text-white text-center text-3xl pb-4 uppercase">
          ip address tracker
        </h1>
        <div class="flex">
          <input
            class="flex-1 py-3 px-2 rounded-tl-md rounded-bl-md focus:outline-none"
            type="text"
            placeholder="请输入IP地址"
            v-model="IP"
          />
          <i
            class="bg-black  text-white px-4 rounded-tr-md rounded-br-md flex items-center fas fa-chevron-right"
            aria-hidden="true"
            @click="getIPLocation"
          ></i>
        </div>
      </div>
      <IPInfo v-if="ipInfo" :ipInfo="ipInfo"></IPInfo>
    </div>
    <!-- map -->
    <div id="map" class="h-full overflow-hidden z-10"></div>
  </div>
</template>

<script>
import IPInfo from '../components/IPInfo'
import leaflet from 'leaflet'
import axios from 'axios'
import { onMounted, ref } from 'vue'
export default {
  name: 'Home',
  components: {
    IPInfo
  },
  setup() {
    let map,
      IP = ref(''),
      ipInfo = ref(null)
    onMounted(() => {
      map = leaflet.map('map').setView([23.036194, 113.777157], 9)
      leaflet
        .tileLayer(
          'https://api.mapbox.com/styles/v1/mapbox/streets-v11/tiles/{z}/{x}/{y}?access_token=pk.eyJ1IjoibGluYmVpMjIiLCJhIjoiY2w2bm93YWNjMDJiZzNjbnNpZnI5cGU0dCJ9.pyCWigIJnyW3kjTuXzW8Aw',
          {
            attribution:
              '© <a href="https://www.mapbox.com/feedback/">Mapbox</a> © <a href="http://www.openstreetmap.org/copyright">OpenStreetMap</a>',
            tileSize: 512,
            zoomOffset: -1
          }
        )
        .addTo(map)
    })
    async function getIPLocation() {
      let ip = IP.value || '27.39.72.114'
      try {
        let {
          data: {
            isp,
            ip: ipAddress,
            location: { timezone, lat, lng, city }
          }
        } = await axios.get(
          `https://geo.ipify.org/api/v2/country,city?apiKey=at_sZ3cXVaitIONLH77nZI92Dsh9VQPQ&ipAddress=${ip}`
        )
        ipInfo.value = {
          isp,
          city,
          timezone,
          ipAddress
        }
        leaflet.marker([lat, lng]).addTo(map)
        map.setView([lat, lng], 13)
      } catch (error) {
        console.log(error)
      }
    }
    return { IP, ipInfo, getIPLocation }
  }
}
</script>
