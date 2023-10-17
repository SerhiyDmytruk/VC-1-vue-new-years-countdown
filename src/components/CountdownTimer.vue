<script setup>
import { reactive, defineAsyncComponent } from 'vue';
const TransitionElement = defineAsyncComponent(() => import('@/TransitionElement.vue'));

let countDownDate = new Date('Dec 31, 2023 23:59:59').getTime();

let timerData = reactive({
  days: 100,
  hours: 60,
  min: 60,
  sec: 60
});

let countForSecond = setInterval(function () {
  let now = new Date().getTime();

  let distance = countDownDate - now;

  timerData.days = Math.floor(distance / (1000 * 60 * 60 * 24));
  timerData.hours = Math.floor((distance % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
  timerData.min = Math.floor((distance % (1000 * 60 * 60)) / (1000 * 60));
  timerData.sec = Math.floor((distance % (1000 * 60)) / 1000);

  if (distance < 0) {
    clearInterval(countForSecond);
  }
}, 1000);
</script>
<template>
  <div>
    <ul class="timer__list">
      <li class="timer__item">
        <span id="days" class="timer__data">{{ timerData.days }}</span> days
      </li>

      <li class="timer__item">
        <span id="hours" class="timer__data"> {{ timerData.hours }} </span> hours
      </li>

      <li class="timer__item">
        <span id="min" class="timer__data">{{ timerData.min }}</span> minutes
      </li>

      <li class="timer__item">
        <span id="sec" class="timer__data">{{ timerData.sec }}</span> seconds

        <TransitionElement>
          <span id="sec" class="timer__data">{{ timerData.sec }}</span> seconds
        </TransitionElement>
      </li>
    </ul>
  </div>
</template>
