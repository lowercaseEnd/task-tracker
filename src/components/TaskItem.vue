<template>
  <li @click="openPage">
    <b-container fluid>
      <b-row>
        <b-col cols="2">
          <p>{{task.name}}</p>
        </b-col>
        <b-col class="column" cols="8">
          <p>{{task.description}}</p>
        </b-col>
        <b-col cols="2">
          <p>{{task.date}}</p>
        </b-col>
      </b-row>
    </b-container>
  </li>
</template>

<script>
export default {
  props: {
    task: {
      type: Object,
      required: true
    }
  },
  methods: {
    openPage() {
      this.$router.push({
        name: "Task Info",
        params: {
          id: this.task.id
        }
      });
    }
  }
};
</script>

<style>
.col-8, .col-2 {
  max-height: 50px;
  word-wrap: break-word;
  overflow: hidden;
}
</style>