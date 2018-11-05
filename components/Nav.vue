<template>
  <nav>
    <ul>
      <li><nuxt-link to="/about">About</nuxt-link></li>
      <li><nuxt-link to="/works">Works</nuxt-link></li>
      <li><nuxt-link to="/contact">Contact</nuxt-link></li>
    </ul>
  </nav>
</template>

<style lang="scss" scoped>
@import '@/assets/style/global.scss';

nav {
  background-color: $subColor;
  padding: 3px;
  border-radius: 10px;
}

ul {
  display: flex;
  align-items: center;
  justify-content: space-evenly;
  line-height: 1;
}

a {
  display: inline-block;
  padding: 3px 12px;
  background-color: $mainColor;
  color: $sub2Color;
  font-weight: bold;
}

.nuxt-link-active {
  background-color: $sub2Color;
  color: $mainColor;
}
</style>
