<template>
  <section>
    <b-form>
      <b-form-group>
        <b-form-select v-model="selected">
          <b-form-select-option value="all">all</b-form-select-option>
          <b-form-select-option value="completed">completed</b-form-select-option>
          <b-form-select-option value="not completed">not completed</b-form-select-option>
        </b-form-select>
      </b-form-group>
    </b-form>
    <ul class="tasks-list">
      
      <task-item  v-for="item in select" :key="item.id" :task="item" />
    </ul>

  </section>
</template>

<script>
const TaskItem = () => import("@/components/TaskItem");

export default {
  data() {
    return {
      tasks: JSON.parse(localStorage.getItem("tasks")),
      selected: "all"
    }
  },
  components: {
    TaskItem
  },
  computed: {
    select() {
      if(this.selected === "completed") {
        return this.tasks.filter(item => item.completed === true);
      }
      if(this.selected === "not completed") {
        return this.tasks.filter(item => item.completed === false);
      }
      if(this.selected === "all") {
        return this.tasks;
      }
    }
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