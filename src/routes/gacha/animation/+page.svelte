<script>
	import GachaponAni from '$lib/components/Gacha/Animation/GachaponAni.svelte';
	import StarSlamAni from '$lib/components/Gacha/Animation/StarSlamAni.svelte';
	import SingleStarSlamAni from '$lib/components/Gacha/Animation/SingleStarSlamAni.svelte';
</script>

<div class="page">
	<SingleStarSlamAni />
	<StarSlamAni />
</div>

<style>
	.page {
		display: flex;
		justify-content: center;
		/* padding: 64px; */
		/* align-items: center; */
		width: 100vw;
		height: 100vh;
		background-color: rgb(74, 74, 74);
	}
</style>
