<template>
	<div class="newTask">
		<input autofocus v-model="task" type="text" @keydown.enter="addTask" placeholder="Tip your new Task" class="formElement">
		<button @click.stop="addTask" class="formElement">+</button>
	</div>
</template>

<script>
export default {
	data() {
		return{
			task: ''
		}
	},

	methods: {
		addTask() {
			this.task == '' ? alert('Empty Task, not able to add') : this.$emit('emitTask', this.task) 
			this.task = ''
		}
	}
}
</script>

<style scoped>
	.newTask {
		margin: 35px
	}

	.formElement {
		outline: none;
		font-size: 1.5rem;
		border: 1px solid white;
		padding: 5px 10px 8px;
		color: white
	}

	input.formElement {
		width: 500px;
		background: #FFF2;
		border-top-left-radius: 16px;
		border-bottom-left-radius: 16px;
	}

	button.formElement {
		border-top-right-radius: 16px;
		border-bottom-right-radius: 16px;
		background: radial-gradient(#a10101, #430247)
	}

	button:hover{
		background: radial-gradient(#c90101, #6e0474);
		cursor: pointer;
	}

	::placeholder { /* Chrome, Firefox, Opera, Safari 10.1+ */
		color: white;
		opacity: .5; /* Firefox */
	}

	:-ms-input-placeholder { /* Internet Explorer 10-11 */
		color: white;
	}

	::-ms-input-placeholder { /* Microsoft Edge */
		color: white;
	}
</style>
