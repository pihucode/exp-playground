<script>
	let circles = Array.from({ length: 100 }, (_, i) => i + 1);
</script>

<div class="particles">
	<div class="vignette__bottom" />
	{#each circles as circle}
		<div class="circles">
			<div class="circle" />
		</div>
	{/each}
</div>

<style lang="scss">
	.vignette__bottom {
		position: absolute;
		bottom: 0;
		width: 100%;
		height: 100%;
		// gradient, fade at top
		background-image: linear-gradient(to bottom, rgba(0, 0, 0, 0) 0%, rgba(0, 0, 0, 0.5) 100%);
	}

	.particles {
		width: 100%;
		height: 40%;
		overflow: hidden;
		position: absolute;
		bottom: 0;
		z-index: 100;
		pointer-events: none;
	}

	.circles {
		$particleNum: 300;
		$particleColor: hsl(180, 100%, 95%);

		position: absolute;
		transform: translateY(-10vh);
		animation-iteration-count: infinite;
		animation-timing-function: linear;

		.circle {
			width: 100%;
			height: 100%;
			border-radius: 50%;
			mix-blend-mode: screen;
			background-image: radial-gradient(
				hsl(180, 100%, 80%),
				hsl(180, 100%, 80%) 10%,
				hsla(180, 100%, 80%, 0) 56%
			);

			animation: fade-frames 1s infinite, scale-frames 2s infinite;

			@keyframes fade-frames {
				0% {
					opacity: 1;
				}
				50% {
					opacity: 0.7;
				}
				100% {
					opacity: 1;
				}
			}

			@keyframes scale-frames {
				0% {
					transform: scale3d(0.4, 0.4, 1);
				}
				50% {
					transform: scale3d(2.2, 2.2, 1);
				}
				100% {
					transform: scale3d(0.4, 0.4, 1);
				}
			}
		}

		$particleBaseSize: 8;

		@for $i from 1 through $particleNum {
			&:nth-child(#{$i}) {
				$circleSize: random($particleBaseSize);
				width: $circleSize + px;
				height: $circleSize + px;

				$startPositionY: random(10) + 100;
				$framesName: 'move-frames-' + $i;
				$moveDuration: 28000 + random(9000) + ms;

				animation-name: #{$framesName};
				animation-duration: $moveDuration;
				animation-delay: random(37000) + ms;

				@keyframes #{$framesName} {
					from {
						transform: translate3d(#{random(100) + vw}, #{$startPositionY + vh}, 0);
					}

					to {
						transform: translate3d(#{random(100) + vw}, #{- $startPositionY - random(30) + vh}, 0);
					}
				}

				.circle {
					animation-delay: random(4000) + ms;
				}
			}
		}
	}
</style>
