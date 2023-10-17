<script setup>
defineProps({
  title: {
    type: String,
    requried: false
  }
});
</script>

<template>
  <h1 class="title">{{ title }}</h1>
</template>
