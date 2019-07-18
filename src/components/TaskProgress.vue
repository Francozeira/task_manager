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

.taskProgress {
  position: relative;
  width: 80%;
  height: 30px;
  border: 2px solid #FFF;
  color: white;
  border-radius: 8px;
  margin-bottom: 15px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.progressBar {
  position: absolute;
  border-radius: 8px;
  height: 100%;
  align-self: flex-start;
  background: linear-gradient(to right,rgba(86, 189, 85, 0.2), rgba(10, 143, 8, 1)), 
  url(https://s3-us-west-2.amazonaws.com/s.cdpn.io/172299/bubbles-mask.gif);
}

.progressValue {
  padding-top: 2px;
  z-index: 1;
  font-size: 1.5rem;
}

</style>
