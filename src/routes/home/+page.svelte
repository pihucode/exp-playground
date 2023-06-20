<script>
	import Home from '$lib/components/Home/Home.svelte';
	import Hover from '$lib/components/Home/Hover.svelte';
	import News from '$lib/components/Home/News.svelte';
</script>

<div class="page">
	<Hover />
	<News />
</div>

<style>
	.page {
		/* display: flex;
		justify-content: center;
		width: 100vw;
		height: 100vh; */
		background-color: rgb(74, 74, 74);
		/* background-image: url('https://mir-s3-cdn-cf.behance.net/project_modules/1400_opt_1/6e13bb66109353.5b0b7773dbca9.jpg'); */
		/* background-image: url('https://i.pinimg.com/originals/eb/c5/34/ebc53433d70de93ba6676e45f5598869.jpg'); */
		/* https://i.pinimg.com/originals/fd/9a/32/fd9a32a61b896d595225375065f4add6.jpg */
		/* background-size: cover; */
	}
</style>
