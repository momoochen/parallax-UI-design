<template>
  <div id ="step-one">
    <transition
      appear
      @before-appear="customBeforeAppearHook"
      @appear="customAppearHook"
    >
      <div id="blue-bg">
        <transition
          appear
          @before-appear="animationBeforeAppearHook"
          @appear="animationAppearHook"
        >
          <div id="svg-circle1">
            <svg 
              width="300" 
              height="300"
            >
              <circle 
                cx="150" 
                cy="100" 
                r="80"
                fill="white"
              />
            </svg>
            <svg 
              width="300" 
              height="300"
            >
              <circle
                cx="10" 
                cy="10" 
                r="100"
                fill="white"
              />
            </svg>
            <svg 
              width="300" 
              height="300"
            >
              <circle
                cx="-150" 
                cy="-50" 
                r="120"
                fill="white"
              />
            </svg>
          </div>
        </transition>
      </div>
    </transition>
    <div class="question-wrapper">
      <div class="question">Q1</div>
      <div class="big-title question-title">“If one day you get a gift that can change the rule of the world, which ability will you choose?” </div>
      <div class="subtitle question-subtitle">Choose the answer appeared in your mind instantly</div>
      <div class="option-wrapper">
        <router-link to="/steptwo">
          <div class="option">Destroy all humans in the world</div>
        </router-link>
        <div class="option">Destroy all humans in the world</div>
        <div class="option">Destroy all humans in the world</div>
      </div>
    </div>
  </div>
</template>



<script>
import Velocity from 'velocity-animate'

export default {
  methods: {
    customBeforeAppearHook: function(el) {
      Velocity(el, { translateX: '100', opacity: 0 }, { duration: 200 })
      // el.style.opacity = 0
    },
    customAppearHook: function(el, done) {
      Velocity(
        el,
        { width: '50%', opacity: 1 },
        { duration: 600 },
        { complete: done }
      )
      // Velocity(el, { opacity: 1, fontSize: '1.4em' }, { duration: 300 })
      // Velocity(el, { fontSize: '1em' }, { complete: done })
    },
    animationBeforeAppearHook: function(el) {
      Velocity(
        el,
        { translateY: '10px', translateX: '10px', opacity: 0 },
        { duration: 600 }
      )
    },

    animationAppearHook: function(el, done) {
      Velocity(
        el,
        {
          translateY: '-500px',
          translateX: '100px',
          scale: '6',
          rotateZ: '180deg',
          opacity: 1
        },
        { duration: 800 }
      )
      Velocity(
        el,
        {
          translateY: '-300px',
          translateX: '50px',
          scale: '1',
          rotateZ: '360deg',
          opacity: 0.3
        },
        { duration: 800 },
        { complete: done }
      )
    }
  }
}
</script>

<style lang="scss" scoped>
#step-one {
  width: 100vw;
  min-height: 100vh;
  position: relative;
}

#blue-bg {
  position: absolute;
  z-index: 1;
  top: 0;
  right: 0;
  background: #29b6f6;
  width: 10px;
  height: 100%;
  overflow: hidden;
}

#svg-circle1 {
  position: absolute;
  z-index: 999;
  bottom: 0;
  right: 0;
  width: 300px;
  height: 300px;

  svg {
    overflow: visible;
  }
}
</style>
