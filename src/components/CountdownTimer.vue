<script setup>
import { ref, reactive } from 'vue';

let countDownDate = new Date('Dec 31, 2023 23:59:59').getTime();
let days = ref();
let hours = ref();
let min = ref();
let sec = ref();

let countForSecond = setInterval(function () {
  let now = new Date().getTime();

  let distance = countDownDate - now;

  days.value = Math.floor(distance / (1000 * 60 * 60 * 24));
  hours.value = Math.floor((distance % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
  min.value = Math.floor((distance % (1000 * 60 * 60)) / (1000 * 60));
  sec.value = Math.floor((distance % (1000 * 60)) / 1000);

  if (distance < 0) {
    clearInterval(countForSecond);
  }
}, 1000);
</script>
<template>
  <div>
    time

    <ul>
      <li>
        <span id="days">{{ days }}</span> days
      </li>

      <li>
        <span id="hours"> {{ hours }} </span> hours
      </li>

      <li>
        <span id="min">{{ min }}</span> minutes
      </li>

      <li>
        <span id="sec">{{ sec }}</span> seconds
      </li>
    </ul>
  </div>
</template>
