<template>
  <header>
    <h1>{{ title }}</h1>
    <!-- Display button, add props to make text and color reusable -->
    <Button
      @btn-click="$emit('show-add-task')"
      :text="setAddTask ? 'Close' : 'Add task'"
      :color="setAddTask ? 'red' : 'green'"
    />
  </header>
</template>

<script>
import Button from './Button.vue'

export default {
  name: 'Header',
  props: {
    title: String,
    setAddTask: Boolean,
  },

  //   Adding the components we want to use
  components: {
    Button,
  },
}
</script>

<style scoped>
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
}
</style>
