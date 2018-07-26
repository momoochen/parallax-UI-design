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
              height="300" 
              width="300"
            >
              <path
                id="tri-angle" 
                d="M120.9 
                181.5c3.3 0 6.3 1.7 8 4.6l36 62.3c1.7 2.9 1.7 6.3 0 9.2-1.7 2.9-4.7 4.6-8 4.6h-72c-3.3 0-6.3-1.7-8-4.6-1.7-2.9-1.7-6.3 0-9.2l36-62.3c1.7-2.9 4.7-4.6 8-4.6m0-1c-3.4 0-6.9 1.7-8.8 5.1l-36 62.3c-3.9 6.8 1 15.3 8.8 15.3h72c7.9 0 12.8-8.5 8.8-15.3l-36-62.3c-1.9-3.4-5.3-5.1-8.8-5.1z" 
                class="st0"
                opacity="0.57"
                fill="#fff"
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
      <div class="question">Q3</div>
      <div class="big-title question-title">“When you’re in a exam which you barely prepared for, which is your priority solution?” </div>
      <div class="subtitle question-subtitle">Choose the answer appeared in your mind instantly</div>
      <div class="option-wrapper">
        <router-link to="/stepfour">
          <div class="option">Take a nap right away</div>
        </router-link>
        <div class="option">Fill the Answer randomly</div>
        <div class="option">All fill the answer "C"</div>
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
