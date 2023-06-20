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
			class:hidden={!isSlideIn && !isSlideOut}
			class="banner__image"
			class:img__slidein__animation={isSlideIn}
			class:img__slideout__animation={isSlideOut}
		>
			<img src={image} alt={altTag} title={attr} />
		</div>

		<div
			class="banner__info"
			class:info__slidein__animation={isSlideIn}
			class:info__slideout__animation={isSlideOut}
		>
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
		/* background-color: orange; */
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

		opacity: 0;
		transform: translateX(100px);
		transition: all 1s ease-in-out;
	}
	.banner__image img {
		width: 100%;
	}

	.img__slidein__animation {
		/* background-color: chartreuse; */

		opacity: 1;
		transform: translateX(0);

		/* animation-name: img_slidein;
		animation-duration: 1s;
		animation-timing-function: ease-out;
		animation-fill-mode: forwards; */
	}
	.img__slideout__animation {
		/* background-color: darkred; */
		animation-name: img_slidein;
		animation-duration: 0.5s;
		animation-timing-function: ease-in-out;
		animation-fill-mode: forwards;
		animation-direction: reverse;
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

		opacity: 0;
		transform: translateX(-50px);
		transition: all 1s ease-in-out;
	}
	.info__slidein__animation {
		opacity: 1;
		transform: translateX(0);

		/* animation-name: info_slidein;
		animation-duration: 1s;
		animation-timing-function: ease-out;
		animation-fill-mode: forwards; */
	}
	.info__slideout__animation {
		animation-name: info_slidein;
		animation-duration: 0.5s;
		animation-timing-function: ease-out;
		animation-fill-mode: forwards;
		animation-direction: reverse;
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
