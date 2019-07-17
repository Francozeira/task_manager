<template>
  <div class="taskProgress">
    <div class="progressValue">{{progress}}%</div>
    <div class="progressBar" :style="{width: progress + '%'}" ></div>
  </div>
</template>

<script>
export default {
	props: {
		progress: {Number , default:0}
	},
};
</script>

<style>
</style>
