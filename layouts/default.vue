<template>
  <div>
    <app-logo/>
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
import AppLogo from '~/components/AppLogo.vue'
import Title from '~/components/Title.vue'
import Nav from '~/components/Nav.vue'
export default {
  components: {
    AppLogo,
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
@import url('https://fonts.googleapis.com/css?family=Sawarabi+Gothic|Unica+One');

$mainColor: #ecf4f3;
$subColor: #76dbd1;
$sub2Color: #57a99a;
$sub3Color: #555151;

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


html {
  font-family: 'Unica One', 'Sawarabi Gothic', sans-serif;
  font-size: 16px;
  word-spacing: 1px;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  box-sizing: border-box;
  background-color: $mainColor;
}

*, *:before, *:after {
  box-sizing: border-box;
  margin: 0;
}

a {
  color: inherit;
  text-decoration: none;
}

ul {
  padding: 0;
}

li {
  list-style-type: none;
}

h2 {
  color: $sub2Color;
}

.main {
  position: fixed;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  width: 90vw;
  height: 80vh;
  margin: auto;
}

.contentsWrap {
  overflow-x: hidden;
  overflow-y: auto;
  height: 75vh;
  margin-top: 2.5vh;
  padding: 2.5vw;
  background-color: rgba(255, 255, 255, .6);
  color: $sub3Color;
}
</style>

