<script setup>
import { ref, onMounted, onUnmounted } from "vue";
import CountdownHeader from "@/components/CountdownHeader.vue";
import CountdownSegment from "@/components/CountdownSegment.vue";

const newYear = new Date('2026-01-01T00:00:00')

const days = ref(0);
const hours = ref(0);
const minutes = ref(0);
const seconds = ref(0);

let timer = null;

function coundownInterval() {
  const now = new Date().getTime();
  const distance = newYear - now;

  if(distance < 0){
    clearInterval(timer)
    days.value = 0;
    hours.value = 0;
    minutes.value = 0;
    seconds.value = 0;
    return;
  }

  days.value = Math.floor(distance / (1000 * 60 * 60 * 24))
  hours.value = Math.floor((distance / (1000 * 60 * 60)) % 24)
  minutes.value = Math.floor((distance / (1000 * 60)) % 60)
  seconds.value = Math.floor((distance / 1000) % 60)
}

onMounted(() => {
  coundownInterval();
  timer = setInterval(coundownInterval, 1000);
})

onUnmounted(() => {
  clearInterval(timer)
})

</script>
<template>
  <div class="app-wrapper">
    <div class="countdown-box">
      <CountdownHeader />
      <main class="flex justify-center">
        <CountdownSegment data-test="days" label="days" :number="days" />
        <CountdownSegment data-test="hours" label="hours" :number="hours" />
        <CountdownSegment data-test="minutes" label="minutes" :number="minutes" />
        <CountdownSegment data-test="seconds" label="seconds" :number="seconds" />
      </main>
    </div>
  </div>
</template>

<style scoped>
.app-wrapper {
  @apply flex items-center justify-center w-full h-full p-10;
}
.countdown-box {
  @apply shadow-md relative bg-white p-5 rounded-lg border-gray-100 border-[1px];
}
body {
  @apply bg-gray-100;
}
</style>
