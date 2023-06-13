<script>
	let bannerImage;

	let animation = 'img__slidein__animation';
	let isSlideIn = false;
	let isSlideOut = false;

	const slideIn = () => {
		reset();
		setTimeout(() => {
			isSlideIn = !isSlideIn;
		}, 10);
	};
	const slideOut = () => {
		reset();
		setTimeout(() => {
			isSlideOut = !isSlideOut;
		}, 10);
	};
	const animate = () => {
		reset();

		isSlideIn = !isSlideIn;
	};
	const reset = () => {
		isSlideIn = false;
		isSlideOut = false;
	};
</script>

<div>
	<h1>asd</h1>
	<div class="controls">
		<button on:click={() => animate()}>Animate</button>
		<button on:click={() => slideIn()}>Slide In</button>
		<button on:click={() => slideOut()}>Slide Out</button>
		<button on:click={() => reset()}>Reset</button>

		<span>Slide In: {isSlideIn}</span>
		<span>Slide out: {isSlideOut}</span>
		<span>isHidden: {!isSlideIn || isSlideOut}</span>
	</div>
	<div class="banner">
		<div
			class="banner__image {animation}"
			class:img__slidein__animation={isSlideIn}
			class:img__slideout__animation={isSlideOut}
			class:hidden={!isSlideIn || !isSlideOut}
			bind:this={bannerImage}
		>
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
	.controls {
		margin-bottom: 200px;
	}
	.hidden {
		display: none;
	}
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
	}
	.banner__image img {
		width: 100%;
	}

	.img__slidein__animation {
		background-color: chartreuse;
		display: block;
		animation-name: img_slidein;
		animation-duration: 1s;
		animation-timing-function: ease-out;
		animation-fill-mode: forwards;
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
	.img__slideout__animation {
		background-color: darkred;
		animation-name: img_slidein;
		animation-duration: 0.5s;
		animation-timing-function: ease-in-out;
		animation-fill-mode: forwards;
		animation-direction: reverse;
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
