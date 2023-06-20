<script>
	import SoftGlowParticles from '$lib/components/Particles/SoftGlowParticles.svelte';

	let entity;
	let shadow;

	// on mousemove, shift the shadow and entity to create a parallax effect
	// the shadow is shifted more than the entity to create a depth effect
	// create a slight delay between mousemove and the actual shift
	const onMouseMove = (e) => {
		const x = e.clientX;
		const y = e.clientY;
		const entityShift = 10;
		const shadowShift = 20;

		entity.style.transform = `translate(${x / entityShift}px, ${y / entityShift}px)`;
		shadow.style.transform = `translate(${x / shadowShift}px, ${y / shadowShift}px)`;
	};
</script>

<div class="container" on:mousemove={onMouseMove}>
	<div class="entity" bind:this={entity}>
		<!-- <img src="https://i.pinimg.com/564x/24/83/58/248358df207fec2ce4e85b9d924cba94.jpg" /> -->
	</div>
	<div class="shadow" bind:this={shadow} />
	<div class="box">placeholder text</div>
	<SoftGlowParticles />
</div>

<style>
	.container {
		position: relative;
		width: 100%;
		height: 100vh;
		background-color: transparent;
		background-image: url('https://mir-s3-cdn-cf.behance.net/project_modules/1400_opt_1/6e13bb66109353.5b0b7773dbca9.jpg');
		background-size: cover;
		/* height: 100vh;
		width: 100vw; */
	}

	.entity {
		position: absolute;
		top: 50px;
		right: 200px;
		z-index: 5;
		width: 400px;
		height: 400px;
		background-color: lightskyblue;
	}
	.entity img {
		width: 200px;
	}

	.shadow {
		position: absolute;
		top: 30px;
		right: 150px;
		z-index: 4;
		width: 300px;
		height: 300px;
		background-color: rgba(0, 0, 0, 0.55);
		filter: blur(10px);
	}

	.entity,
	.shadow {
		transition: transform 0.25s linear;
	}

	.box {
		position: absolute;
		top: 50%;
		left: 50%;
		z-index: 3;
		width: 800px;
		height: 420px;
		background-color: whitesmoke;
		transform: translate(-50%, -50%);
	}
</style>
