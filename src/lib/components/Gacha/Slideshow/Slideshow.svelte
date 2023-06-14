<script>
	/*
    Ref: https://svelte.dev/repl/7c0339d9aeb64b8c9b4bf402c71d791e?version=3.29.0
    */

	import { images } from './data.js';
	import Slide from './Slide.svelte';
	import Thumbnail from './Thumbnail.svelte';
	import Caption from './Caption.svelte';
	import BannerSlide from './BannerSlide.svelte';

	/* IMAGE TO SHOW */
	let isAnimating = false;
	let imageShowingIndex = 0;
	// $: console.log(imageShowingIndex);
	// $: image = images[imageShowingIndex];

	let isSlideIn = true;
	let isSlideOut = false;
	let image = images[imageShowingIndex];

	const reset = () => {
		isSlideIn = false;
		isSlideOut = false;
	};
	const slideIn = () => {
		reset();
		setTimeout(() => {
			isSlideIn = true;
		}, 10);
	};
	const slideOut = () => {
		reset();
		setTimeout(() => {
			isSlideOut = true;
		}, 10);
	};

	$: {
		slideOut();
		setTimeout(() => {
			image = images[imageShowingIndex];
			slideIn();
		}, 900);

		// // slide out animation
		// console.log('slide out');
		// isSlideOut = true;
		// // wait for the animation to finish
		// setTimeout(() => {
		// 	console.log('reset');
		// 	isSlideOut = false;
		// 	isSlideIn = true;

		// 	setTimeout(() => {
		// 		// console.log('slide in');
		// 		// isSlideIn = true;
		// 	}, 0.1 * 1000);
		// }, 1 * 1000);

		// console.log('change image');
		// image = images[imageShowingIndex];
		// isSlideIn = true;

		// setTimeout(() => {
		// 	isSlideOut = false;
		// 	isSlideIn = false;
		// }, 0.1 * 1000);
	}

	const nextSlide = () => {
		if (imageShowingIndex === images.length - 1) {
			imageShowingIndex = 0;
		} else {
			imageShowingIndex += 1;
		}
	};

	const prevSlide = () => {
		if (imageShowingIndex === 0) {
			imageShowingIndex = images.length - 1;
		} else {
			imageShowingIndex -= 1;
		}
	};

	const goToSlide = (number) => {
		imageShowingIndex = number;
	};
</script>

<div class="slideshow">
	<!-- image gallery -->
	<div class="container">
		<!-- <Slide image={image.imgurl} altTag={image.name} attr={image.attribution} /> -->
		<BannerSlide
			image={image.imgurl}
			altTag={image.name}
			attr={image.attribution}
			{isSlideIn}
			{isSlideOut}
			animation="img__slidein__animation"
		/>
	</div>

	<!-- Image text -->
	<Caption
		caption={images[imageShowingIndex].name}
		on:prevClick={prevSlide}
		on:nextClick={nextSlide}
	/>

	<!-- Thumbnail images -->
	<div class="thumbnails-row">
		{#each images as { id, imgurl, name, attribution }}
			<Thumbnail
				thumbImg={imgurl}
				altTag={name}
				titleLink={attribution}
				{id}
				selected={imageShowingIndex === id}
				on:click={() => goToSlide(id)}
			/>
		{/each}
	</div>
</div>

<style>
	@import url('https://fonts.googleapis.com/css2?family=Josefin+Sans:wght@500&display=swap');

	* {
		box-sizing: border-box;
		font-family: 'Josefin Sans', sans-serif;
	}

	.slideshow {
		width: 800px;
		display: flex;
		flex-direction: column;
		margin: 10% auto;
		background-color: #222;
	}

	/* Position the image container (needed to position the left and right arrows) */
	.container {
		position: relative;
	}

	.thumbnails-row {
		height: 100px;
		width: 100%;
		display: flex;
		align-self: flex-end;
	}
</style>
