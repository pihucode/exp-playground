<script>
	let bannerImage;

	const playAnimation = () => {
		console.log('playAnimation called!');
		// reset animation
		bannerImage.style.animation = 'none';
		bannerImage.offsetHeight; /* trigger reflow */
	};
</script>

<div>
	<h1>asd</h1>
	<div class="controls">
		<button on:click={playAnimation()}>Play animation</button>
	</div>
	<div class="banner">
		<div class="banner__image" bind:this={bannerImage}>
			<img src="/images/Character_Yanqing_Splash_Art.png" alt="banner image" />
		</div>

		<div class="banner__info">
			<div class="banner__info__title">
				<h2>Title</h2>
			</div>
			<div class="banner__info__description">
				<p>Description Lorem ipsum...</p>
			</div>
		</div>
	</div>
</div>

<style>
	.banner {
		/* display: flex; */
		/* flex-direction: row; */
		position: relative;
		width: 800px;
		height: 450px;
		background-color: lightgray;
		color: black;
	}

	.banner__image {
		position: absolute;
		top: -150px;
		z-index: 1;

		/* background-color: lightseagreen; */
		width: 600px;
		height: 450px;

		animation-name: img_slidein;
		animation-duration: 1s;
		animation-timing-function: ease-out;
		animation-fill-mode: forwards;
	}
	.banner__image img {
		width: 100%;
	}
	@keyframes img_slidein {
		from {
			opacity: 0;
			margin-left: 100px;
		}
		to {
			opacity: 1;
			margin-left: 0;
		}
	}

	.banner__info {
		position: absolute;
		bottom: 0px;
		right: 0px;
		z-index: 5;

		background-color: cadetblue;
		width: 300px;
		padding: 8px 24px;
		margin: 32px;

		animation-name: info_slidein;
		animation-duration: 1s;
		animation-timing-function: ease-out;
		animation-fill-mode: forwards;
	}

	@keyframes info_slidein {
		from {
			opacity: 0;
			margin-right: 100px;
		}

		to {
			opacity: 1;
			margin-right: 32px;
		}
	}

	.banner__info__title {
	}

	.banner__info__description {
	}
</style>
