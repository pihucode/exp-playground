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
		font-size: 1.2rem;
	}
	.box__main {
		position: absolute;
		top: 50%;
		left: 50%;
		width: 45%;
		height: 40%;
		transform: translate(-50%, -50%);
		background-color: rgb(138, 216, 241);
	}

	.box1 {
		position: absolute;
		top: 5%;
		left: 4%;
		width: 10%;
		height: 15%;
		background-color: rgb(245, 123, 123);
	}
	.box2 {
		position: absolute;
		left: 5rem;
		bottom: 4.2rem;
		width: 11.5rem;
		height: 6.5rem;
		background-color: rgb(172, 248, 79);
	}
	.box3 {
		position: absolute;
		top: 45%;
		right: 10%;
		width: 12%;
		height: 14%;
		background-color: rgb(145, 123, 245);
	}
</style>
