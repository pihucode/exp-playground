<script>
	export let image;
	export let altTag;
	export let attr;
</script>

<!-- Full-width images with number text -->
<div class="mySlides">
	<img src={image} alt={altTag} title={attr} />
</div>

<style>
	img {
		width: 100%;
	}
</style>
