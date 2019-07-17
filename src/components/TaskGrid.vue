<template>
  <div class="taskGrid">
    <template v-if="tasks.length > 0">
      <Task v-for="(task, i) in tasks" :key="task.text" :task="task"
        @changePending="$emit('changePending',i)"
        @deleteTask="$emit('deleteTask',i)"
      ></Task>
    </template>
    <p v-else class="noTask">You really have outdone yourself this time! =D</p>
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

.NoTask {
  color: #aaa;
  font-size: 2rem;
}
</style>
