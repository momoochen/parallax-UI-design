<template>
  <transition
    appear
    @before-appear="animationBeforeAppearHook"
    @appear="animationAppearHook"
  >
    <div id="svg-square">
      <svg 
        width="100" 
        height="100"
      >
        <rect 
          x="-100" 
          y="50" 
          rx="20" 
          ry="20" 
          width="280" 
          height="280"
          style="fill:white"
        />
      </svg>
      <svg 
        width="300" 
        height="300"
      >
        <rect 
          x="0" 
          y="0" 
          rx="20" 
          ry="20" 
          width="300" 
          height="300"
          style="fill:#29b6f6"
        />
      </svg>
      <svg 
        width="300" 
        height="300"
      >
        <circle
          cx="0" 
          cy="0" 
          r="200"
          fill="#18144d"
        />
      </svg>
      <svg 
        width="100" 
        height="100"
      >
        <rect 
          x="-50" 
          y="-100" 
          rx="20" 
          ry="20" 
          width="100" 
          height="100"
          style="fill:white"
        />
      </svg>
      <svg 
        width="200" 
        height="200"
      >
        <circle
          cx="100" 
          cy="100" 
          r="80"
          fill="#18144d"
        />
      </svg>
    </div>
  </transition>
</template>

<script>
import Velocity from 'velocity-animate'

export default {
  methods: {
    animationBeforeAppearHook: function(el) {
      Velocity(
        el,
        { translateY: '500px', translateX: '0px', opacity: 0 },
        { duration: 600 }
      )
    },

    animationAppearHook: function(el, done) {
      Velocity(
        el,
        {
          translateY: '0px',
          translateX: '0px',
          scale: '8',
          rotateZ: '315deg',
          opacity: 0.9
        },
        { duration: 1200 }
      )
      Velocity(
        el,
        {
          translateY: '0px',
          translateX: '0px',
          scale: '2',
          rotateZ: '-315deg',
          opacity: 0.8
        },
        { duration: 1200, loop: 2 }
      )
      Velocity(
        el,
        {
          translateY: '2000px',
          translateX: '100px',
          scale: '1',
          rotateZ: '360deg',
          opacity: 1
        },
        { duration: 800 },
        { complete: done }
      )
    }
  }
}
</script>

<style lang="scss" scoped>
#svg-square {
  width: 100%;
  height: 100%;
}
svg {
  overflow: visible;
}
</style>
