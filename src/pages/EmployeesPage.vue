<template>
  <h2>{{ header }}</h2>
  <p>{{ content }}</p>
</template>

<script>

export default {
  name: 'EmployeesPage',
  computed: {
    header () {
      return this.$route.params.id ? 'Employee detail page' : 'Employees list'
    },
    content () {
      return this.$route.params.id ? 'this is a detail page ' : 'this is list of all guys'
    }
  }
}

</script>