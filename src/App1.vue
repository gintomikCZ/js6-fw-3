<template>

<h1>js6-fw-3</h1>
<TNavBar :links="links" />

<RouterView>

</RouterView>

<p>another fix content</p>
<div>
  <TButton label="print $route" @clicked="onClickedRoute"/>
  <TButton label="print $router" @clicked="onClickedRouter"/>
</div>
<div>
  <TButton label="go to Contact Page" @clicked="$router.push('/contact')"/>
</div>
<div>
  <TButton label="go forward" @clicked="$router.go(1)"/>
</div>

</template>

<script>

import TNavBar from '@/components/TNavBar.vue'
import TButton from '@/components/TButton.vue'
export default {
  name: 'App',
  data () {
    return {
      links: [
        { path: '/', label: 'Home' },
        { path: '/about', label: 'About' },
        { path: '/contact', label: 'Contact' }
      ]
    }
  },
  methods: {
    onClickedRoute () {
      console.log(this.$route)
    },
    onClickedRouter () {
      console.log(this.$router)
    }
  },
  components: { TNavBar, TButton }
}

</script>

<style scoped>

</style>