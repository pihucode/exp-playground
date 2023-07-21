<script>
	import StarIcon from '$lib/svg/StarIcon.svelte';
	let isAnimate = true;

	const animate = () => {
		isAnimate = false;
		setTimeout(() => {
			isAnimate = true;
		}, 1000 * 0.5);
	};
</script>

<div class="container">
	<div class="controls">
		<button on:click={() => animate()}>Play Animation</button>

		<div>isAnimate: {isAnimate}</div>
	</div>

	<div class:star__animation={isAnimate} class="bg">
		<StarIcon fill="white" />
	</div>
</div>

<style>
	.container {
		padding: 50px;
	}

	.bg {
		background-color: darkseagreen;
	}

	.star__animation {
		animation: starslam 0.3s ease-in forwards;
	}

	@keyframes starslam {
		0% {
			scale: 3;
			opacity: 0;
		}
		100% {
			scale: 1;
			opacity: 1;
		}
	}
</style>
