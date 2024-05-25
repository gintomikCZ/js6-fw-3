<template>
  <nav>
  <!-- <ul>
    <li>
      <RouterLink to="/">Home</RouterLink>
    </li>
    <li>
      <RouterLink to="/about">About us</RouterLink>
    </li>
    <li>
      <RouterLink to="/contact">Contact</RouterLink>
    </li>
  </ul> -->
  <ul>
    <li v-for="link in links">

      <div v-if="$route.path === link.path">{{ link.label }}</div>
      <RouterLink v-else :to="link.path">{{ link.label }}</RouterLink>

    </li>
  </ul>
</nav>
</template>

<script>

export default {
  name: 'TNavBar',
  props: {
    links: Array // pole objektů {path: '/about', label: 'About us' }
  }
}

</script>

<style scoped>
a {
  color: red;
}

nav ul {
  list-style-type: none;
  display: flex;
  margin: 0;
  padding: 0;
  gap: 2rem;
}
</style>