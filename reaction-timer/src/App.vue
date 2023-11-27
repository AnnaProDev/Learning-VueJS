<template> <div>
	<h1>My Reaction Timer</h1>
   <button class="btn" @click="start" :disabled="isPlaying">PLAY</button>
	<Block v-if="isPlaying" :delay="delay" @end="endGame"/>
	<Results v-if="showResults" :score="score"/>
</div>

</template>

<script>
import Block from './components/Block.vue'
import Results from './components/Results.vue'

export default {
  name: 'App',
  components: { Block, Results },
  data() {
	return {
		isPlaying: false,
		delay: null,
		score: null,
		showResults: false,
	}
  },
  methods: {
	start() {
		this.delay = 2000 + Math.random() * 5000
		this.isPlaying = true
	},
	endGame(reactionTime) {
		this.showResults = true;
		this.score = reactionTime;
		this.isPlaying = false;
	} 
  },
}
</script>

<style>
	#app {
	font-family: Avenir, Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	text-align: center;
	color: #444;
	margin-top: 60px;
	}
	h1 {
		color: #15bf94;
	}

	.btn {
		padding: 10px 30px;
		font-weight: bold;
		font-size: 16px;
		letter-spacing: 1px;
		color: #fff;
		background: linear-gradient(90deg, #00E0FF 1.82%, #00FFA3 100%);
		border-radius: 10px;
		border: 1px solid #15bf94;
		transition: all 0.3s ease;
		cursor: pointer;
	}
	button:hover {
		background: linear-gradient(60deg, #00E0FF 1.82%, #00FFA3 30%);
		box-shadow: 0 0 7px rgba(21, 191, 148, 0.5);
		border: 1px solid #00FFA3;

	}

	button:disabled {
		background: linear-gradient(90deg, #00E0FF 1.82%, #00FFA3 100%);
		cursor:not-allowed;
		box-shadow:none;
		opacity: 0.2;
	}
</style>
