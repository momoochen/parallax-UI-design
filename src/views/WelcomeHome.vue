<template>
  <div id="home">
    <div id="wrapper">
      <div class="big-title">GEOMETRY PERSON</div>
      <div class="subtitle">Find Your Core Personality Type in Shapes!</div>
      <router-link to="/stepone">
        <button 
          class="button" 
        >START</button>
      </router-link>
    </div>
    <FinalAnimation id="final-animation" />
  </div>
</template>

<script>
import FinalAnimation from '@/components/FinalAnimation'
export default {
  components: {
    FinalAnimation
  }
}
</script>

<style lang="scss" scoped>
#home {
  width: 100vw;
  min-height: 100vh;
  padding: 50px;
  margin: 0 auto;
  text-align: center;
  position: relative;
  overflow: hidden;

  #wrapper {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    display: flex;
    margin: auto auto;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    z-index: 999;
    .big-title {
      font-size: 88px;
    }
    .subtitle {
      margin-top: 12px;
      font-size: 28px;
      font-family: 'Asap', sans-serif;
    }
    .button {
      width: 200px;
      height: 44px;
      border-radius: 44px;
      border: none;
      padding: 8px 12px;
      background: rgb(53, 75, 199);
      color: white;
      font-size: 20px;
      letter-spacing: 0.8px;
      font-family: 'Dosis', sans-serif;
      margin-top: 20px;
      transition: all 1s ease-in-out;
      cursor: pointer;
      &:hover {
        background: rgb(39, 52, 129);
      }
    }
    a {
      text-decoration: none;
    }
  }
  #final-animation {
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    position: absolute;
    z-index: 2;
  }
}
</style>
