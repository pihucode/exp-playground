<script></script>

<div class="container">
	<div class="box__main">main content</div>
	<div class="box1">box 1 content</div>
	<div class="box2">box 2 content</div>
	<div class="box3">box 3 content</div>
</div>

<style>
	.container {
		position: relative;
		width: 100%;
		height: 100%;
		overflow: hidden;
		font-size: 1rem;
	}
	.box__main {
		position: absolute;
		top: 50%;
		left: 50%;
		width: 25rem;
		height: 16rem;
		transform: translate(-50%, -50%);
		background-color: rgb(138, 216, 241);
	}

	.box1 {
		position: absolute;
		top: 1.2rem;
		left: 1.6rem;
		width: 5rem;
		height: 5rem;
		background-color: rgb(245, 123, 123);
	}
	.box2 {
		position: absolute;
		left: 3rem;
		bottom: 3.2rem;
		width: 11.5rem;
		height: 6.5rem;
		background-color: rgb(172, 248, 79);
	}
	.box3 {
		position: absolute;
		top: 13rem;
		right: 2rem;
		width: 10rem;
		height: 6rem;
		background-color: rgb(145, 123, 245);
	}
</style>
