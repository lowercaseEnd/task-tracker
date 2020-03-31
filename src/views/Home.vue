<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <task-info />
  </div>
</template>

<script>
// @ is an alias to /src
import TaskInfo from "@/components/TaskInfo";

export default {
  name: 'Home',
  components: {
    TaskInfo
  }
}
</script>
