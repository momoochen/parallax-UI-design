<template>
  <transition 
    name="router-animation" 
    enter-active-class="animated fadeIn" 
    leave-active-class="animated fadeOutUp"
    mode="out-in"
  >
    <router-view />
  </transition>
</template>

<script>
export default {}
</script>

<style lang="scss" scoped>
.animated {
  animation-duration: 0.6s;
}
</style>
