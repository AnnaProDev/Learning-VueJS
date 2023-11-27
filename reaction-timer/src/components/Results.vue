<template> 
	<div>
		<p class="result">Reaction time: {{ score }} ms</p>
		<p class="rank"> {{ rank }}</p>
	</div>
</template>

<script>
export default {
	props: ['score'],
	data() {
		return {
			rank: null,
		}
	},
	mounted() {
		if ( this.score < 250) {
			this.rank = 'Ninja Fingers'
		} else if ( this.score < 400) {
			this.rank = 'Ninja Fingers'
		} else {
			this.rank = "Snail pace ..."
		}
	}

}

</script>

<style>
	.result {
		color: #e21f1f;
		font-weight: bold;
		font-size: 20px;
	}
	.rank {
		color: #15bf94;
		font-weight: bold;
		font-size: 24px;
	}
</style>