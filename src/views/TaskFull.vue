<template>
  <section>
    <p>Task name: {{task.name}}</p>
    <p>Tags: </p>
    <div v-for="tag in task.tags" :key="tag">
      <p>{{tag}}</p>
    </div>
    <p>Completed: {{task.completed}}</p>
    <b-form>
      <b-form-group>
        <b-form-textarea v-model="description" size="lg"></b-form-textarea>
      </b-form-group>
      <b-form-group>
        <b-form-datepicker v-model="date" />
      </b-form-group>
      <b-button @click="changeTask">Изменить</b-button>
    </b-form>
    <b-button @click="toggleStatus">
      <div v-if="this.task.completed">Открыть</div>
      <div v-else>Завершить</div></b-button>
  </section>
</template>

<script>
export default {
  data() {
    return {
      task: "",
      description: "",
      date: ""
    };
  },
  mounted() {
    let temp = JSON.parse(localStorage.getItem("tasks"));
    for (let item of temp) {
      if (item.id === Number(this.$route.params.id)) {
        this.task = item;
        this.description = item.description;
        this.date = item.date;
        break;
      }
    }
  },
  methods: {
    changeTask() {
      this.task.description = this.description;
      this.task.date = this.date;
    },
    toggleStatus() {
      this.task.completed = !this.task.completed;
    }
  }
};
</script>