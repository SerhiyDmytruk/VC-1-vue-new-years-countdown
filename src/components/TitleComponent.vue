<script setup>
defineProps({
  title: {
    type: String,
    requried: false
  }
})
</script>

<template>
  <h1>{{ title }}</h1>
</template>
