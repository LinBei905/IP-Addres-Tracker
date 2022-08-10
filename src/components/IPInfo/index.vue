<template>
  <div
    class="absolute flex flex-col -bottom-64 lg:-bottom-20 lg:flex-row bg-white gap-y-4 gap-x-12
    px-8 pt-8 pb-12 rounded-md shadow-md"
  >
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
  components: {
    InfoItem
  },
  setup() {
    return {}
  }
}
</script>
