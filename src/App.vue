<script setup>
import TitleComponent from './components/TitleComponent.vue'

import CountdownTimer from './components/CountdownTimer.vue'
</script>

<template>
  <header>
    <TitleComponent title="New Years Countdown" />
  </header>
  <main>
    <CountdownTimer />
  </main>
</template>

<style scoped>
header {
  line-height: 1.5;
}
</style>
