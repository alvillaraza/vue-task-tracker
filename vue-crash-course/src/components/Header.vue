<template>
  <header>
    <h1>{{ title }}</h1>
    <!-- v-show="homePage" removes the Add Task button from the About Page -->
    <Button v-show="homePage"
      @btn-click="$emit('toggle-add-task')"
      :text="showAddTask ? 'Close' : 'Add Task'"
      :color="showAddTask ? 'red': 'green'"
    />
  </header>
</template>

<script>
import Button from "./Button";
export default {
  name: "Header",
  props: {
    title: String,
    showAddTask: Boolean,
  },
  components: {
    Button,
  },
  computed: {
    // this removes the Add Task button from the About Page
    homePage(){
      if(this.$route.path === '/'){
        return true

      } else {
        return false
      }
    }
  }
};
</script>

<style scoped>
header {
  display: flex;
  justify-content: space-between;
  align-content: center;
  margin-bottom: 20px;
}
</style>
