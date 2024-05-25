<template>
  <button @click="onClick" :disabled="isDisabled">{{  label  }}</button>
</template>

<script>

export default {
  name: 'TButton',
  props: {
    label: String,
    isDisabled: Boolean
  },
  methods: {
    onClick() {
      this.$emit('clicked')
    }
  }
}

</script>

<style scoped>
button:disabled {
  cursor: not-allowed;
  background: white;
  border: none;
}
</style>