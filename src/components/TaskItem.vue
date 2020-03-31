<template>
  <li @click="openPage">
    <p>{{task.id}}</p>
    <p>{{task.date}}</p>
  </li>
</template>

<script>
export default {
  props: {
    task: {
      type: Object,
      required: true,
    }
    
  },
  methods: {
    openPage() {
      this.$router.push({
        name: "Task Info",
        params: {
          id: this.task.id
        }
      })
    }
  }
}
</script>