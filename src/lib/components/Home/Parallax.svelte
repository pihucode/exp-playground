<script>
	document.addEventListener('mousemove', parallax);
	function parallax(event) {
		this.querySelectorAll('.parallax-wrap span').forEach((shift) => {
			const position = shift.getAttribute('value');
			const x = (window.innerWidth - event.pageX * position) / 90;
			const y = (window.innerHeight - event.pageY * position) / 90;

			shift.style.transform = `translateX(${x}px) translateY(${y}px)`;
		});
	}
</script>

<div class="container">
	<div class="parallax-wrap">
		<span value="-15" />
		<span value="5" />
		<h2>test</h2>
	</div>
</div>

<style>
	.container {
		margin: 0;
		height: 100vh;
		background-color: whitesmoke;
		overflow: hidden;
	}
	.parallax-wrap {
		position: relative;
		width: 100%;
		height: 100vh;
		overflow: hidden;
		display: flex;
		justify-content: center;
		align-items: center;
	}
	.parallax-wrap h2 {
		position: relative;
		font-size: 100px;
		color: white;
		z-index: 2;
		text-align: center;
	}

	.parallax-wrap span {
		position: absolute;
		height: 20px;
		width: 30px;
		border-radius: 100%;
	}
</style>
