<template>
  <section>
    <b-form @submit.prevent>
      <legend>Создание задачи</legend>
      <b-form-group label="Task name">
        <b-form-input v-model="name" type="text" id="task-name" placeholder="Название" required />
      </b-form-group>
      <b-form-group label="Task tags">
        <b-form-tags v-model="tags" type="text" id="task-tags" remove-on-delete/>
      </b-form-group>
      <b-form-group label="Task description">
        <b-form-textarea v-model="description" name id="task-description" cols="30" rows="10">Описание</b-form-textarea>
      </b-form-group>
      <b-form-group label="Pick date">
        <b-form-datepicker id="task-date" v-model="date" />
        <p>{{date}}</p>
      </b-form-group>
      <b-button @click="saveTask">Сохранить</b-button>
    </b-form>
  </section>
</template>

<script>
export default {
  data() {
    return {
      name: "",
      tags: [],
      description: "",
      date: ""
    }
  },
  methods: {
    saveTask() {
      let temp = JSON.parse(localStorage.getItem("tasks")) || [];
      temp.push({
        id: Date.now(),
        name: this.name,
        tags: this.tags,
        description: this.description,
        date: this.date,
        completed: false
      });
      this.name = this.description = this.date = "";
      this.tags = [];
      localStorage.setItem("tasks", JSON.stringify(temp));
    }
  }
}
</script>