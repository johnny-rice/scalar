<script setup lang="ts">
import { ScalarIcon } from '@scalar/components'
import { useRoute } from 'vue-router'

const currentRoute = useRoute()
</script>
<template>
  <div
    class="flex flex-1 flex-col rounded-lg rounded-b-none rounded-r-none pt-0 h-full bg-b-2 relative darkmode-subpage-wrapper">
    <div
      class="lg:min-h-header items-center w-full p-1 t-app__top-container flex items-center">
      <router-link
        class="text-c-2 text-sm font-medium ml-1 flex items-center p-1.5 hover:bg-b-3 rounded cursor-pointer gap-0.5 active:text-c-1 no-underline dark:hover:bg-b-2"
        :to="`/workspace/${currentRoute.params.workspace}/request/default`">
        <ScalarIcon
          icon="ChevronLeft"
          size="md"
          thickness="1.75" />
        <span class="leading-none">Back To Requests</span>
      </router-link>
    </div>
    <slot />
  </div>
</template>
<style scoped>
.dark-mode .darkmode-subpage-wrapper {
  background-color: color-mix(in srgb, var(--scalar-background-1), black);
}
</style>
