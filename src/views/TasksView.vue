<template>
  <section>
    <ul class="tasks-list">
      <task-item v-for="item in tasks" :key="item.id" :task="item" />
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
.tasks-list {
  list-style: none;
  padding: 0;
  margin: 0;
}
</style>