<template>
  <div id="container-wrapper">
    <div class="pinContainer">
      <section
        v-for="(p, index) in panels"
        :class="`panel-${index}`"
        :style="{backgroundColor: p.bgColor}"
        :key="index"
        class="panel"
      >
        <div class="step">
          <div class="container-wrapper">
            <div class="big-title">{{ p.title }}</div>
            <div class="subtitle">{{ p.subtitle }}</div>
          </div>
        </div>
        <FinalAnimation 
          v-if="index ===0" 
          class="final-animation"
        />
        <router-link 
          v-if="index ===2" 
          to="/stepone"
        >
          <button 
            v-if="index ===2" 
            class="button"
          >Try Again</button>
        </router-link>
      </section>
    </div>
  </div>
</template>


<script>
import Velocity from 'velocity-animate'
import FinalAnimation from '@/components/FinalAnimation'

export default {
  components: {
    FinalAnimation
  },
  data() {
    return {
      panels: [
        {
          title: 'ALL DONE!',
          subtitle: 'Keep scrolling to show the result',
          bgColor: 'rgb(250, 90, 149)'
        },
        {
          title: 'YOU ARE…',
          subtitle: 'Keep scrolling to show the result',
          bgColor: '#29b6f6'
        },
        {
          title: 'TRIANGLE',
          subtitle: 'Your personality type is',
          button: 'Try again',
          bgColor: '#66bb6a'
        }
      ]
    }
  },
  mounted() {
    this.$nextTick(this.pinContainerScene)
  },
  destroyed() {
    // Destroy ScrollMagic when our component is removed from DOM
    this.$ksvuescr.$emit('destroy')
  },
  methods: {
    pinContainerScene() {
      const Length = this.panels.length

      // Create a new Timeline (equivalent to new TimelineMax())
      const tl = new this.$gsap.TimelineMax()

      for (var i = 0; i < Length; i++) {
        // For each panel in this.panels array:
        let animFrom
        switch (i) {
          case 0:
            break
          case 1:
            animFrom = { x: '-100%' } // Second panel comes from the left
            break
          case 2:
            animFrom = { x: '100%' } // Third one comes from the right
            break
          case 3:
            animFrom = { y: '-100%' } // Finally, the last one comes from the top
            break
        }
        if (i !== 0) {
          // For each panel except the one whom index is 0, create the tween and add it to the tl timeline.
          // (To use GSAP easings, just prefix their name with this.$gsap)
          tl.fromTo(`section.panel-${i}`, 1.5, animFrom, {
            x: '0%',
            y: '0%',
            ease: this.$gsap.Linear.easeNone
          })
        }
      }

      // create scene and set its params
      const scene = new this.$scrollmagic.Scene({
        triggerElement: '.pinContainer',
        triggerHook: 'onLeave',
        duration: `${Length * 100}%`
      })
        .setPin('.pinContainer')
        .setTween(tl)

      // Add scene to ScrollMagic controller by emiting an 'addScene' event on vm.$ksvuescr (which is our global event bus)
      this.$ksvuescr.$emit('addScene', 'pinContainerScene', scene)
    },
    animationBeforeAppearHook: function(el) {
      Velocity(
        el,
        { translateY: '10px', translateX: '10px', opacity: 0 },
        { duration: 600 }
      )
    }
  }
}
</script>

<style lang="scss" scoped>
.pinContainer {
  width: 100%;
  height: 100vh;
  overflow: hidden;
  position: relative;
}
.panel {
  height: 100%;
  width: 100%;
  position: absolute;
  top: 0;
  left: 0;
  display: flex;
  justify-content: center;
  align-items: center;
  color: white;
  z-index: 1;
}
.step {
  top: 0;
  left: 0;
  height: 100%;
  width: 100%;
  position: absolute;
  z-index: 99;
  .container-wrapper {
    height: 100%;
    width: 100%;
    margin: auto auto;
    text-align: center;
    display: flex;
    justify-content: center;
    flex-direction: column;
    align-items: center;
    .big-title {
      font-size: 88px;
    }
    .subtitle {
      margin-top: 12px;
      font-size: 28px;
      font-family: 'Asap', sans-serif;
    }
  }
}

.button {
  margin: 0 auto;
  width: 200px;
  height: 44px;
  border-radius: 44px;
  border: none;
  padding: 8px 12px;
  background: rgb(53, 75, 199);
  color: white;
  font-size: 20px;
  font-family: 'Dosis', sans-serif;
  margin-top: 260px;
  transition: all 1s ease-in-out;
  cursor: pointer;
  &:hover {
    background: rgb(39, 52, 129);
  }
}
a {
  text-decoration: none;
}

.final-animation {
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  position: absolute;
  z-index: 2;
}
</style>
