<script>
	import StarIcon from '$lib/svg/StarIcon.svelte';
	import { onMount } from 'svelte';

	let icons = [];
	const totalIcons = 5;
	let currentIndex = 0;

	onMount(() => {
		for (let i = 0; i < totalIcons; i++) {
			icons.push({ index: i, isAnimate: false, isHidden: true });
		}
	});

	const animate = () => {
		// Reset the currentIndex when all icons have been animated
		if (currentIndex >= icons.length) {
			currentIndex = 0;
			// hide all the icons
			icons.forEach((icon) => {
				icon.isHidden = true;
			});
		}

		// Animate the current icon and update the currentIndex
		icons[currentIndex].isHidden = false;
		icons[currentIndex].isAnimate = true;

		// Wait for the animation to end and then trigger the next one
		setTimeout(() => {
			icons[currentIndex].isAnimate = false;
			currentIndex++;
			animate();
		}, 1000 * 0.5);
	};
</script>

<div class="container">
	<div class="controls">
		<button
			on:click={() => {
				animate();
			}}
		>
			Play Animation
		</button>
	</div>

	<div class="stars">
		{#each icons as icon}
			<div class="bg" class:star__animation={icon.isAnimate} class:hide={icon.isHidden}>
				<StarIcon fill="white" />
			</div>
		{/each}
	</div>
</div>

<style>
	.container {
		padding: 50px;
	}

	.stars {
		display: flex;
		flex-direction: row;
	}

	.star__animation {
		animation: starslam 0.3s ease-in forwards;
	}

	.hide {
		visibility: hidden;
	}

	@keyframes starslam {
		0% {
			transform: scale(4);
			translate: 50px, 20px;
			rotate: -320deg;
			opacity: 0;
		}
		50% {
			rotate: -200deg;
		}
		100% {
			transform: scale(1);
			translate: 0, 0;
			rotate: 0deg;
			opacity: 1;
		}
	}

	.bg {
		background-color: darkseagreen;
	}
</style>
