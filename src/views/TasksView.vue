<template>
  <section>
    <ul v-for="item in tasks" :key="item.id">
      <task-item :task="item" />
    </ul>
  </section>
</template>

<script>
const TaskItem = () => import("@/components/TaskItem");

export default {
  data() {
    return {
      tasks: JSON.parse(localStorage.getItem("tasks"))
    }
  },
  components: {
    TaskItem
  }
}
</script>

<style>

</style>