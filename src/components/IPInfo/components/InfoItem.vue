<template>
  <div class="flex flex-col">
    <h3 class="text-xl mb-2 uppercase">{{ title }}</h3>
    <span class="text-2xl">{{ content }}</span>
  </div>
</template>

<script>
export default {
  props: ['title', 'content'],
  setup() {
    return {}
  }
}
</script>
