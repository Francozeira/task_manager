<template>
	<div @click="$emit('changePending',task)" class="task" :class="stateClass">
		<div>{{task.text}}</div>
		<span @click.stop="$emit('deleteTask',task)" class="close">x</span>
	</div>
</template>

<script>
export default {
	props: {
		task: {type: Object, required:true}
	},

	computed: {
		stateClass() {
			return {
				pending: this.task.pending,
				done: !this.task.pending
			}
		}
	},

	data() {
		return{

		}
	}
}
</script>

<style scoped>

	.task {
		position: relative;
		box-sizing: border-box;
		width: 250px;
		height: 80px;
		padding: 10px;
		border-radius: 16px;
		font-size: 1.5rem;
		cursor: pointer;
		user-select: none;
		display: flex;
		justify-content: center;
		align-items: center; 
	}

	.pending {
		border-left: 12px solid #B73229;
		background-color: #F44336;
	}

	.done {
		color: #DDD;
		border-left: 12px solid #0A8F08;
		background-color: #4CAF50;
		text-decoration: line-through;		
	}

	.pending .close {
		background: #B73229;
	}

	.done .close {
		background: #0A8F08;
	}

	.close {
		position: absolute;
		right: 8px;
		top: 8px;
		font-size: .8rem;
		height: 16px;
		width: 16px;
		border-radius: 10px;
		display: flex;
		justify-content: center;
	}
</style>
