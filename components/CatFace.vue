<template>
  <div>
    <div class="catFace" :style="blur" :class="{move: isMoving}" @click="moveEye">
      <img src="@/assets/svg/face.svg" width="160" height="160" class="face">
      <img src="@/assets/svg/eyes.svg" width="160" height="160" class="eyes">
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      blurStyle: {
        'filter': 'blur(2px)',
        'z-index': -1
      },
      isMoving: false,
    }
  },
  computed: {
    blur () {
      return this.$route.path === '/' ? '' : this.blurStyle
    },
  },
  methods: {
    moveEye () {
      this.isMoving = !this.isMoving
    }
  }
}
</script>

<style lang="scss" scoped>
@import '@/assets/style/global.scss';

img {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  margin: auto;
}

p {
  text-align: center;
  color: #57a99a;
}

.move .face {
  animation-name: face;
  animation-duration: .3s;
  animation-timing-function: ease;
  animation-iteration-count: infinite;
}

.move .eyes {
  animation-name: eyes;
  animation-duration: .3s;
  animation-timing-function: ease;
  animation-iteration-count: infinite;
}

@keyframes face {
  25% {
    transform: translateY(2px);
  }
  50% {
    transform: translateY(-2px);
  }
  75% {
    transform: translateY(2px);
  }
  100% {
    transform: translateY(-2px);
  }
}

@keyframes eyes {
  15% {
    transform: translateX(2px);
  }
  40% {
    transform: translateX(-2px);
  }
  65% {
    transform: translateX(2px);
  }
  90% {
    transform: translateX(-2px);
  }
}

.catFace {
  display: inline-block;
  /* animation: turn 2s linear forwards 1s; */
  /* transform: rotateX(180deg); */
  position: fixed;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  margin: auto;
  overflow: hidden;
  width: 160px;
  height: 160px;
  z-index: 1;
}
</style>

