<script setup lang="ts">
import ScreenClock from '~/components/screen/clock.vue'
import ScreenControls from '~/components/screen/controls.vue'
import ScreenFunctions from '~/components/screen/functions.vue'
import { useScreenStore } from '~/stores/screen'

defineComponent({ name: 'Screen' })

const screenStore = useScreenStore()

const htmlAttrs = computed(() => ({ class: screenStore.contrast }))

useHead({ htmlAttrs })
</script>

<template>
  <div
    class="flex h-full flex-col justify-between bg-slate-100 text-slate-950 dark:bg-slate-900 dark:text-slate-100"
    :style="{ opacity: screenStore.brightness }"
  >
    <div class="h-[600px] p-2">
      <div class="flex h-full justify-between">
        <div class="h-full w-full overflow-auto">
          <slot />
        </div>
        <div class="flex w-[200px] flex-col gap-y-4">
          <ScreenClock />
          <ScreenFunctions />
        </div>
      </div>
    </div>
    <ScreenControls />
  </div>
</template>
