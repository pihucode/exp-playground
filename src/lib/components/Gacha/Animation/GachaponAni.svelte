<script>
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

		<span>isAnimate: {isAnimate}</span>
	</div>

	<div class="gachapon">
		<img src="/images/Character_Yanqing_Splash_Art.png" alt="banner" />
		<img
			class:img__animation={isAnimate}
			src="/images/Character_Yanqing_Splash_Art.png"
			alt="overlay"
		/>
	</div>
</div>

<style>
	.container {
		padding: 32px;
		position: relative;
		width: 500px;
	}

	.gachapon img {
		position: absolute;
		top: 100px;
		left: 0;
		width: 500px;
		pointer-events: none;
	}

	.img__animation {
		animation: fadeout 0.3s ease-in forwards;
	}

	@keyframes fadeout {
		0% {
			scale: 1;
			opacity: 1;
		}
		100% {
			scale: 1.4;
			opacity: 0;
		}
	}
</style>
