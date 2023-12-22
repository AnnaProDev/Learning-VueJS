<template>
  <div class="block" v-if="showBlock" @click="stopTimer">
	CLICK ME
  </div>
</template>

<script>
export default {
	props: ['delay'], //Take props
	data() {
		return {
			showBlock: false, 
			timer: null,
			reactionTime: 0,// Track the amount of time it takes for the user to click on the square
		}
	},
	mounted() { 
		setTimeout( () => { //Wait delay
			this.showBlock = true; //Show block after delay is up
			this.startTimer()
		}, this.delay) //We pass in this delay as a prop
	},
	methods: {
		startTimer() {
			this.timer = setInterval( () => {
				this.reactionTime += 10; // We're timing the reaction time in steps of 10 ms  
			}, 10)
		},
		stopTimer() {
			clearInterval(this.timer) //Stop and clear timer
			this.$emit('end', this.reactionTime) //Custom event
		},
	},
};

</script>

<style>
	.block {
		width: 400px;
		border-radius: 20px;
		background: #15bf94;
		color: #fff;
		font-weight: bold;
		text-align: center;
		padding: 100px 0;
		margin: 40px auto;
		font-size: 20px;
	}
</style>