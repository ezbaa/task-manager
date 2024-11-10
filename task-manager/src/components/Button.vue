<template>
  <button @click="onClick" :style="{ background: color }" class="btn">{{ text }}</button>
</template>

<script>
export default {
  // Exporting the button and adding the props
  name: 'Button',
  props: {
    text: String,
    color: String,
  },
  //   Function for the button click
  methods: {
    onClick() {
      this.$emit('btn-click')
    },
  },
}
</script>

<style scoped></style>
