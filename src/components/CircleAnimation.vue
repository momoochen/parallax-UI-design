<template>
  <svg 
    xmlns="http://www.w3.org/2000/svg" 
    xmlns:xlink="http://www.w3.org/1999/xlink" 
    viewBox="0 0 826 768"
  >
    <g id="a">
      <defs>
        <circle 
          id="SVGID_1_" 
          cx="134.1" 
          cy="669.9" 
          r="52.1"
          fill="#fff"
          opacity="0.57"
        />
      </defs>
      <use 
        fill="#fff" 
        overflow="visible" 
        xlink:href="#SVGID_1_"
      />
      <clipPath id="SVGID_2_">
        <use 
          overflow="visible" 
          xlink:href="#SVGID_1_"
        />
      </clipPath>
    </g>
    <g id="b">
      <g 
        id="XMLID_3_" 
        class="st0"
      >
        <circle 
          fill="#fff"
          cx="272.8" 
          cy="544.9" 
          r="52.1" 
          class="st1"
          opacity="0.57"
        />
      </g>
    </g>
    <g id="c">
      <g 
        id="XMLID_2_" 
        class="st0"
      >
        <circle
          opacity="0.57"
          fill="#fff"
          cx="411.5" 
          cy="669.9" 
          r="52.1" 
          class="st1"
        />
      </g>
    </g>
    <g id="d">
      <g 
        id="XMLID_5_" 
        class="st0"
      >
        <circle
          opacity="0.57"
          fill="#fff"
          cx="550.2" 
          cy="544.9" 
          r="52.1" 
          class="st1"
        />
      </g>
    </g>
    <g id="e">
      <g 
        id="XMLID_7_" 
        class="st0"
      >
        <circle
          opacity="0.57"
          fill="#fff"
          cx="688.9" 
          cy="669.9" 
          r="52.1" 
          class="st1"
        />
      </g>
    </g>
  </svg>
</template>

<script>
export default {}
</script>

<style lang="scss" scoped>
#a {
  animation: a;
  animation-duration: 5s;
  animation-iteration-count: infinite;
  animation-timing-function: linear;
  transform-origin: 50% 50%;
}
@keyframes a {
  0% {
    transform: scale(1) translateY(0);
  }
  25% {
    transform: scale(1.1) translateY(-150px);
  }
  50% {
    transform: scale(1.12) translateY(-300px);
  }
  75% {
    transform: scale(1.1) translateY(-150px);
  }
  100% {
    transform: scale(1) translateY(0);
  }
}

#b {
  animation: a;
  animation-duration: 6s;
  animation-iteration-count: infinite;
  transform-origin: center;
}

@keyframes b {
  0% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(-80px);
  }
  100% {
    transform: translateY(0);
  }
}

#c {
  animation: a;
  animation-duration: 12s;
  animation-iteration-count: infinite;
  transform-origin: center;
}

#d {
  animation: a;
  animation-duration: 12s;
  animation-iteration-count: infinite;
  transform-origin: center;
}

#e {
  animation: a;
  animation-duration: 12s;
  animation-iteration-count: infinite;
  transform-origin: center;
}

@keyframes c {
  0% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(-120px);
  }
  100% {
    transform: translateY(0);
  }
}

svg {
  overflow: visible;
}
</style>
