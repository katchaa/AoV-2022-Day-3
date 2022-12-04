<script setup>
defineProps({
  label: String,
  number: Number,
})
</script>
<template>
  <div class="flex flex-col items-center gap-2">
    <div class="overflow-hidden w-20 h-10 relative">
      <Transition name="segment" mode="out-in">
        <span :key="number" class="text-green text-4xl absolute top-0 left-[50%] -translate-x-1/2">{{ number }}</span>
      </Transition>
    </div>
    <label class="text-base">{{ label }}</label>
  </div>
</template>
<style>
.segment-enter-from {
  opacity: 0;
}

.segment-leave-to {
  opacity: 0;
}

.segment-enter-active,
.segment-leave-active,
.segment-move {
  transition: all 0.4s ease-in;
}
</style>
