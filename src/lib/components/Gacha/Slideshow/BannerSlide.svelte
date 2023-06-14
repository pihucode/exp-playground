<script>
	import { onMount, onDestroy } from 'svelte';

	export let image;
	export let altTag;
	export let attr;
	export let animation;
	export let isSlideIn;
	export let isSlideOut;

	let bannerImage;
</script>

<div>
	<h1>asd</h1>
	<div class="banner">
		<div
			bind:this={bannerImage}
			class="banner__image"
			class:img__slidein__animation={isSlideIn}
			class:img__slideout__animation={isSlideOut}
			class:hidden={!isSlideIn && !isSlideOut}
		>
			<img src={image} alt={altTag} title={attr} />
		</div>

		<div class="banner__info">
			<div class="banner__info__title">
				<h2>{attr}</h2>
			</div>
			<div class="banner__info__description">
				<p>isSlideIn: {isSlideIn}</p>
				<p>isSlideOut: {isSlideOut}</p>
			</div>
		</div>
	</div>
</div>

<style>
	.hidden {
		/* display: none; */
		opacity: 0.5;
		background-color: orange;
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
		/* background-color: chartreuse; */
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
		/* background-color: darkred; */
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
