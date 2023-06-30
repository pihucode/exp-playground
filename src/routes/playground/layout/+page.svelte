<script>
	import MobileLayout from '$lib/components/Playground/MobileLayout.svelte';
	let page;

	function adjustZoom() {
		page.style.zoom = '1';
	}
</script>

<div class="page" bind:this={page} on:load={adjustZoom}>
	<MobileLayout />
</div>

<style>
	.page {
		width: 100vw;
		height: 56.25vw; /* 100/56.25 = 1.778 */
		max-height: 100vh;
		max-width: 177.78vh; /* 16/9 = 1.778 */
		background-color: #021027;
		margin: auto;
		position: absolute;
		top: 0;
		bottom: 0; /* vertical center */
		left: 0;
		right: 0; /* horizontal center */
	}
</style>
