<template>
  <div class="flex flex-col h-screen max-h-screen">
    <!-- nav -->
    <div class="flex justify-center relative bg-hero-pattern px-4 pt-8 pb-32">
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
          />
          <i
            class="bg-black  text-white px-4 rounded-tr-md rounded-br-md flex items-center fas fa-chevron-right"
            aria-hidden="true"
          ></i>
        </div>
      </div>
      <IPInfo></IPInfo>
    </div>
  </div>
</template>

<script>
import IPInfo from '../components/IPInfo'
export default {
  name: 'Home',
  components: {
    IPInfo
  }
}
</script>
