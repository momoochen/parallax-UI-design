<template>
  <div id="app">
    <transition 
      name="router-animation" 
      enter-active-class="animated fadeIn" 
      leave-active-class="animated fadeOutUp"
      mode="out-in"
    >
      <router-view />
    </transition>
  </div>
</template>

<script>
export default {}
</script>

<style lang="scss">
#app {
  width: 100vw;
  min-height: 100vh;
}

.enter-active-class {
  animation: fadeIn 0.5s;
}
</style>
