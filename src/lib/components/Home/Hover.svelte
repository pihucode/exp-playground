<script>
	import SoftGlowParticles from '$lib/components/Particles/SoftGlowParticles.svelte';

	let entity;
	let shadow;

	let mainTitle = 'Nekolotl';
	let subTitle = 'An adoptables gacha';
	let about =
		'Official website for Nekolotls. A closed species adoptables gacha game currently in the works.';

	// on mousemove, shift the shadow and entity to create a parallax effect
	// the shadow is shifted more than the entity to create a depth effect
	// create a slight delay between mousemove and the actual shift
	const onMouseMove = (e) => {
		const x = e.clientX;
		const y = e.clientY;
		const entityShift = 20;
		const shadowShift = 15;

		entity.style.transform = `translate(${x / entityShift}px, ${y / entityShift}px)`;
		entity.style.filter = `drop-shadow(${50 + x / shadowShift}px ${
			30 + y / shadowShift
		}px 10px rgba(0, 0, 0, 0.4))`;
		// shadow.style.transform = `translate(${x / shadowShift}px, ${y / shadowShift}px)`;
	};
</script>

<div class="container" on:mousemove={onMouseMove}>
	<div class="entity" bind:this={entity}>
		<img style="transform: scaleX(-1);" src="/images/relic-seeker.png" alt="featured nekolotl" />
	</div>
	<!-- <div class="shadow" bind:this={shadow} /> -->

	<div class="box__left">
		<h1 class="title">{mainTitle}</h1>
		<p class="subtitle">{subTitle}</p>
		<p class="about">{about}</p>
		<div class="button__container">
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
		overflow: hidden;
	}

	.entity {
		position: absolute;
		bottom: 100px;
		left: 50vw;
		z-index: 20;
	}
	.entity img {
		width: 800px;
		max-width: 1000px;
		filter: drop-shadow(0 0 5px rgba(0, 0, 0, 0.25));
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
		/* transition: transform 0.25s linear; */
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
		/* left: 100px; */
		left: 10em;
		bottom: 32px;
		z-index: 10;
		/* width: 40vw; */
		width: 600px;
		max-width: 800px;
		max-height: 600px;
		/* background-color: rgba(0, 0, 0, 0.15); */
		color: white;
		background-image: linear-gradient(
			to bottom,
			rgba(0, 0, 0, 0.25),
			rgba(0, 0, 0, 0.05),
			rgba(0, 0, 0, 0)
		);
		border-radius: 6px;
		font-family: 'Open Sans', sans-serif;
		padding: 32px 64px;
		padding-bottom: 200px;
	}

	.title {
		font-size: 4em;
		font-weight: bold;
		text-transform: uppercase;
		margin: 32px 0;
	}
	.btn {
		background-color: transparent;
		border: 1px solid white;
		color: white;
		padding: 8px 16px;
		margin: 0 8px;
		font-size: 16px;
		font-weight: bold;
		cursor: pointer;
		transition: all 0.25s linear;
		border-radius: 2px;
	}
	.btn:hover {
		background-color: white;
		color: gray;
	}
</style>
