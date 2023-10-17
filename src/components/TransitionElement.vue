<template>
  <Transition name="fade" mode="in-out">
    <slot />
  </Transition>
</template>

<style scoped>
.v-enter-active,
.v-leave-active,
.v-enter-active .modal-wrapper-inner,
.v-leave-active .modal-wrapper-inner {
  transition: all 0.5s ease;
}

.v-enter-from,
.v-leave-to {
  opacity: 0;
}

.v-enter-from .modal-wrapper-inner,
.v-leave-to .modal-wrapper-inner {
  transform: translateY(-50px);
}

.slide-up-enter-active,
.transition-demo .slide-up-leave-active {
  transition: all 0.25s ease-out;
}

.slide-up-enter-from {
  opacity: 0;
  transform: translateY(30px);
}

.slide-up-leave-to {
  opacity: 0;
  transform: translateY(-30px);
}
</style>
