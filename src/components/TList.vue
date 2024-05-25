<template>
  <ul>
    <li v-for="item in items">{{ item }}</li>
  </ul>
</template>
<script>

export default {
  name: 'TList',
  props: {
    items: {
      type: Array,
      validator: (v) => v.every(item => typeof item === 'string')
    }
  }
}

</script>

<style scoped>
ul {
  list-style-type: none;
}

</style>