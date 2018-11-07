<template>
  <div>
    <cat-face/>
    <Title/>
    <div class="main">
      <transition-group name="fade" tag="div">
        <Nav key="nav" v-show="isShow"/>
        <div class="contentsWrap" key="contentsWrap" v-show="isShow">
          <transition name='slide'>
            <nuxt class="contents"/>
          </transition>
        </div>
      </transition-group>
    </div>
  </div>
</template>

<script>
import CatFace from '@/components/CatFace.vue'
import Title from '@/components/Title.vue'
import Nav from '@/components/Nav.vue'
export default {
  components: {
    CatFace,
    Title,
    Nav
  },
  transition: {
    name: 'fade',
    mode: 'out-in'
  },
  computed: {
    isShow () {
      return this.$route.path !== '/'
    }
  }
}
</script>

<style lang="scss">
@import '@/assets/style/main.scss';
@import '@/assets/style/global.scss';

.fade-enter-active {
  animation: fade-in .2s;
}
.fade-leave-active {
  animation: fade-in .2s reverse;
}
@keyframes fade-in {
  0% {
    transform: scale(0.95);
    opacity: 0;
  }
  100% {
    transform: scale(1);
    opacity: 1;
  }
}

.slide-enter-active {
  animation: slide-in .4s;
}
.slide-leave-active {
  animation: slide-in .4s reverse;
}
@keyframes slide-in {
  0% {
    transform: translateX(100%);
    opacity: 0;
  }
  50% {
    transform: translateX(-2%);
  }
  75% {
    transform: translateX(0.5%);
  }
  100% {
    transform: translateX(0);
    opacity: 1;
  }
}

.main {
  position: fixed;
  top: 10vh;
  right: 0;
  bottom: 0;
  left: 0;
  width: 90vw;
  margin: auto;
}

.contentsWrap {
  overflow-x: hidden;
  overflow-y: auto;
  -webkit-overflow-scrolling: touch;
  height: 75vh;
  margin-top: 2.5vh;
  padding: 2.5vw;
  background-color: rgba(255, 255, 255, .6);
  color: $sub3Color;
}
</style>

