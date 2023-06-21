<script>
	import SoftGlowParticles from '$lib/components/Particles/SoftGlowParticles.svelte';

	let entity;
	let shadow;

	let textAbout =
		'Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.';

	// on mousemove, shift the shadow and entity to create a parallax effect
	// the shadow is shifted more than the entity to create a depth effect
	// create a slight delay between mousemove and the actual shift
	const onMouseMove = (e) => {
		const x = e.clientX;
		const y = e.clientY;
		const entityShift = 20;
		const shadowShift = 10;

		entity.style.transform = `translate(${x / entityShift}px, ${y / entityShift}px)`;
		shadow.style.transform = `translate(${x / shadowShift}px, ${y / shadowShift}px)`;
	};
</script>

<div class="container" on:mousemove={onMouseMove}>
	<div class="entity" bind:this={entity}>
		<img src="/images/Character_Yanqing_Splash_Art.png" alt="image" />

		<!-- <img src="https://i.pinimg.com/564x/24/83/58/248358df207fec2ce4e85b9d924cba94.jpg" /> -->
	</div>
	<div class="shadow" bind:this={shadow} />

	<div class="box__left">
		<h1 class="title">Main title here</h1>
		<p class="subtitle">Subtitle here lorem ipsum</p>
		<p class="about">{textAbout}</p>
		<div class="button">
			<button class="btn">button 1</button>
			<button class="btn">button 2</button>
		</div>
	</div>

	<SoftGlowParticles />
</div>

<style>
	@import url('https://fonts.googleapis.com/css2?family=Open+Sans:ital,wght@0,400;0,600;0,700;1,400;1,600;1,700&display=swap');

	.container {
		position: relative;
		width: 100%;
		height: 100vh;
		background-color: transparent;
		background-image: url('https://mir-s3-cdn-cf.behance.net/project_modules/1400_opt_1/6e13bb66109353.5b0b7773dbca9.jpg');
		background-size: cover;
	}

	.entity {
		position: absolute;
		top: -100px;
		right: 50px;
		z-index: 20;
	}
	.entity img {
		width: 800px;
	}

	.shadow {
		position: absolute;
		top: 30px;
		right: 150px;
		z-index: 15;
		width: 300px;
		height: 300px;
		background-color: rgba(0, 0, 0, 0.25);
		filter: blur(10px);
	}

	.entity,
	.shadow {
		transition: transform 0.25s linear;
	}

	.box__centered {
		position: absolute;
		top: 50%;
		left: 50%;
		z-index: 10;
		width: 800px;
		height: 420px;
		background-color: whitesmoke;
		transform: translate(-50%, -50%);
	}
	.box__left {
		position: absolute;
		left: 100px;
		bottom: 32px;
		z-index: 10;
		max-width: 800px;
		max-height: 600px;
		/* background-color: rgba(0, 0, 0, 0.15); */
		color: white;
		background-image: linear-gradient(to bottom, rgba(0, 0, 0, 0.25), rgba(0, 0, 0, 0.05));
		font-family: 'Open Sans', sans-serif;
	}

	.title {
		font-size: 150px;
		font-weight: bold;
		text-transform: uppercase;
		margin: 32px 0;
	}
</style>
