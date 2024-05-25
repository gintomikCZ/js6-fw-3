<template>
  <h2>{{  header  }}</h2>
  <main>{{  content  }}</main>
</template>

<script>

export default {
  name: 'TPage',
  props: {
    header: String,
    content: String
  }
}

</script>