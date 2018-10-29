<template>
  <div>
    <h2>About me</h2>
    <ul>
      <li v-for="item in profile" :key="item.title">
        <dl>
          <dt>{{ item.title }}</dt>
          <dd>{{ item.detail }}</dd>
        </dl>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      profile: [
        {
          title: 'Name',
          detail: '村松純太'
        },
        {
          title: 'Birthday',
          detail: '1993/1/24'
        },
        {
          title: 'Job',
          detail: 'Frontend Engineer'
        }
      ]
    }
  },
  // beforeCreate () {
  //   console.log('beforeCreate')
  // },
  // created () {
  //   console.log('created')
  // },
  // beforeMount () {
  //   console.log('beforeMount')
  // },
  // mounted () {
  //   console.log('mounted')
  // },
  // beforeUpdate () {
  //   console.log('beforeUpdate')
  // },
  // updated () {
  //   console.log('updated')
  // },
  // beforeDestroy () {
  //   console.log('beforeDestroy')
  // },
  // destroyed () {
  //   console.log('destroyed')
  // }
}
</script>



<style scoped>
dl {
  display: flex;
  align-items: baseline;
}

dt {
  white-space: nowrap;
}

dt:after {
  content: ':';
  display: inline-block;
  margin-right: .5em;
}
</style>
