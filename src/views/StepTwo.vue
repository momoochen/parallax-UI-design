<template>
  <div id ="step">
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
          <div id="svg-circle">
            <svg 
              width="300" 
              height="300"
            >
              <rect 
                x="-10" 
                y="0" 
                rx="20" 
                ry="20" 
                width="200" 
                height="200"
                style="fill:white"
              />
            </svg>
            <svg 
              width="300" 
              height="300"
            >
              <rect 
                x="150" 
                y="-30" 
                rx="20" 
                ry="20" 
                width="250" 
                height="250"
                style="fill:white"
              />
            </svg>
            <svg 
              width="100" 
              height="100"
            >
              <rect 
                x="20" 
                y="-50" 
                rx="20" 
                ry="20" 
                width="100" 
                height="100"
                style="fill:white"
              />
            </svg>
            <svg 
              width="100" 
              height="100"
            >
              <rect 
                x="100" 
                y="20" 
                rx="20" 
                ry="20" 
                width="150" 
                height="150"
                style="fill:white"
              />
            </svg>
          </div>
        </transition>
      </div>
    </transition>
    <div class="question-wrapper">
      <div class="question">Q2</div>
      <div class="big-title question-title">“Imagine you’re almost late, but totally lost at a forked road. Which way do you prefer to go?” </div>
      <div class="subtitle question-subtitle">Choose the answer appeared in your mind instantly</div>
      <div class="option-wrapper">
        <router-link to="/stepthree">
          <div class="option">The left one</div>
        </router-link>
        <div class="option">The right one</div>
        <div class="option">Open Google Map</div>
      </div>
    </div>
  </div>
</template>



<script>
import Velocity from 'velocity-animate'

export default {
  methods: {
    customBeforeAppearHook: function(el) {
      Velocity(el, { translateX: '-100', opacity: 0 }, { duration: 200 })
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
#step {
  width: 100%;
  height: 100%;
  position: relative;
  display: flex;
  justify-content: flex-end;
}

#blue-bg {
  position: absolute;
  z-index: 1;
  top: 0;
  left: 0;
  background: #66bb6a;
  width: 10%;
  height: 100%;
  overflow: hidden;
}

.step-two {
  position: absolute;
  top: 0;
  right: 0;
  z-index: 999;
}

#svg-circle {
  position: absolute;
  z-index: 999;
  bottom: 0;
  left: 0;
  width: 300px;
  height: 300px;

  svg {
    overflow: visible;
  }
}
</style>
