<template>
  <div
    class="absolute flex flex-col -bottom-64 lg:-bottom-20 lg:flex-row bg-white gap-y-4 gap-x-12
    px-8 pt-8 pb-12 rounded-md shadow-md"
  >
    <InfoItem></InfoItem>
    <InfoItem></InfoItem>
    <InfoItem></InfoItem>
    <InfoItem></InfoItem>
  </div>
</template>

<script>
import InfoItem from './components/InfoItem.vue'
export default {
  components: {
    InfoItem
  },
  setup() {
    return {}
  }
}
</script>
