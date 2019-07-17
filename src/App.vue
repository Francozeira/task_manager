<template>
  <div id="app">
    <h1>A Simple Task Manager</h1>
		<TaskProgress :progress="progress"/>
    <NewTask @emitTask="addTask" />
    <TaskGrid :tasks="tasks" @deleteTask="taskDeleter" @changePending="pendingChanger" />
  </div>
</template>

<script>
import NewTask from './components/NewTask.vue';
import TaskGrid from './components/TaskGrid.vue';
import TaskProgress from './components/TaskProgress'

export default {
  components: { TaskProgress, NewTask, TaskGrid },
	
	computed:{
		
	},

  data() {
    return {
      tasks: [
        { text: 'Buy contact lenses', pending: true },
        { text: 'Give your jumps', pending: false },
        { text: 'Pay College tuition because i am an American', pending: true },
        { text: 'Check on intern contract', pending: true },
        { text: 'Hit the Gym!', pending: false }
			]
    };
  },

  methods: {
    addTask(data) {
      const sameName = t => t.text === data;
      const reallyNew = this.tasks.filter(sameName).length == 0;

      reallyNew
        ? this.tasks.push({ text: data, pending: true })
        : alert('Task allready created');
    },

    taskDeleter(i) {
      this.tasks.splice(i, 1);
		},
	
		pendingChanger(i) {
			this.tasks[i].pending = !this.tasks[i].pending
		}
  }
};
</script>

<style>
body {
  background: #200122; /* fallback for old browsers */
  background: -webkit-linear-gradient(
    to right,
    #6f0000,
    #200122
  ); /* Chrome 10-25, Safari 5.1-6 */
  background: linear-gradient(
    to right,
    #6f0000,
    #200122
  ); /* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */
  color: #fff;
  font-family: 'Comfortaa', cursive;
}

#app {
  display: flex;
  flex: 1;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

#app h1 {
  margin-bottom: 5px;
  font-size: 3rem;
  font-family: 'Lobster', cursive;
  user-select: none;
}
</style>
