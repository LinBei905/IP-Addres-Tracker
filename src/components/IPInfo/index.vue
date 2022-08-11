<template>
  <div
    class="absolute flex flex-col -bottom-80 lg:-bottom-20 lg:flex-row bg-white gap-y-4 gap-x-12
    px-8 pt-8 pb-12 rounded-md shadow-md"
  >
    <i
      class="right-0 top-0 pr-2 text-gray-400 text-2xl absolute flex items-center fas fa-times"
      aria-hidden="true"
      @click="$emit('reset')"
    ></i>
    <InfoItem title="IP地址" :content="ipInfo.ipAddress"></InfoItem>
    <InfoItem title="位置" :content="ipInfo.city"></InfoItem>
    <InfoItem title="时区" :content="`UTC${ipInfo.timezone}`"></InfoItem>
    <InfoItem title="ISP" :content="ipInfo.isp"></InfoItem>
  </div>
</template>

<script>
import InfoItem from './components/InfoItem.vue'

export default {
  props: ['ipInfo'],
  emits: ['reset'],
  components: {
    InfoItem
  },
  setup() {
    return {}
  }
}
</script>
