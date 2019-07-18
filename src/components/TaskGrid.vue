<template>
  <div class="taskGrid">
    <template v-if="tasks.length > 0">
      <Task v-for="(task, i) in tasks" :key="task.text" :task="task"
        @changePending="$emit('changePending',i)"
        @deleteTask="$emit('deleteTask',i)"
      ></Task>
    </template>
    <div v-else>
      <img src="https://i.imgflip.com/1k37ih.jpg" alt="You have really outdone yourself this time! =D">
    </div>
  </div>
</template>

<script>
import Task from './Task.vue';
export default {
  components: {
    Task
  },

  props: {
    tasks: { type: Array, required: true }
  },

  data() {
    return {};
  }
};
</script>

<style scoped>
.taskGrid {
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
}

.taskGrid .task {
  margin: 10px;
}

img {
  border: 10px solid rgba(221, 221, 221, 0.3);
  border-radius: 10px;
}
</style>
