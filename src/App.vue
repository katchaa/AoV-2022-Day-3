<script setup>
import { computed } from 'vue'
import CountdownHeader from '@/components/CountdownHeader.vue'
import CountdownSegment from './components/CountdownSegment.vue'
import { useNow } from '@vueuse/core'

const now = useNow()
const christmas = new Date('12/24/2022 00:00:00')

// Days
const daysCount = computed(() => {
  const day = 1000 * 60 * 60 * 24
  return (christmas - now.value) / day
})
const daysRound = computed(() => {
  return Math.floor(daysCount.value)
})

// Hours
const hoursCount = computed(() => {
  return 24 * (daysCount.value - daysRound.value)
})
const hoursRound = computed(() => {
  return Math.floor(hoursCount.value)
})

// Minutes
const minutesCount = computed(() => {
  return 60 * (hoursCount.value - hoursRound.value)
})
const minutesRound = computed(() => {
  return Math.floor(minutesCount.value)
})

// Seconds
const secondsCount = computed(() => {
  return 60 * (minutesCount.value - minutesRound.value)
})
const secondsRound = computed(() => {
  return Math.floor(secondsCount.value)
})
</script>
<template>
  <div class="w-full h-full flex justify-center items-center">
    <div>
      <div class="shadow-md bg-white p-5 rounded-lg border-gray-100 border-[1px]">
        <CountdownHeader />
        <main class="flex justify-center items-center">
          <CountdownSegment label="days" :number="daysRound" />
          <CountdownSegment label="hours" :number="hoursRound" />
          <CountdownSegment label="minutes" :number="minutesRound" />
          <CountdownSegment label="seconds" :number="secondsRound" />
        </main>
      </div>
      <h4 class="mt-10 text-gray-400 text-center text-sm">
        This challenge brought to you by <a href="https://vueschool.io/" class="underline">Vue School</a>
      </h4>
    </div>
  </div>
</template>

<style>
body {
  @apply bg-gray-100;
}
</style>
