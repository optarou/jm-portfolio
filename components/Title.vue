<template>
  <h1 :class="isHome"><nuxt-link :to="titleLink">{{ title }}</nuxt-link></h1>
</template>

<script>
export default {
  data () {
    return {
      title: 'J.M.Portfolio'
    }
  },
  computed: {
    titleLink () {
      return this.$route.path === '/' ? '/about' : '/'
    },
    isHome () {
      return this.$route.path === '/' ? 'home' : ''
    }
  },
  methods: {
  }
}
</script>

<style lang="scss" scoped>
@import '@/assets/style/global.scss';

h1 {
  position: fixed;
  top: 3vh;
  right: 0;
  left: 0;
  color: $sub2Color;
  font-size: 4vh;
  text-align: center;
  letter-spacing: .2em;
  transition: transform .2s ease;
  z-index: 1;
}

.home {
  color: $subColor;
  transform: scale(1.2) translateY(100%);
}

a {
  text-decoration: none;
  color: inherit;
}
</style>
