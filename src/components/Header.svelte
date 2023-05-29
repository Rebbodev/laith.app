<script lang="ts">
</script>

<div id="placeholder">
	<div id="main-div">
		<div class="left-side">
			<a href="/" id="heart">❤︎</a>
			<a href="/projects">Projects</a>
			<a href="/blog">Blog</a>
			<a href="/skills">Skills</a>
		</div>
		<div class="right-side" />
	</div>
</div>

<style lang="scss">

	#placeholder{
		position: sticky;
		top: 0;
		z-index: 9999;
		background-color: $black;
		box-shadow: 0 0 50px 0 $black;
	
	#main-div {
		height: 4rem;
		width: 40rem;

		display: flex;
		align-items: center;

		margin-inline: auto;
		margin-top: 4rem;
		margin-bottom: 20px;
		padding: 5px;

		.left-side {
			height: inherit;
			width: auto;
			display: flex;
			align-items: center;

			#heart {
				font-size: 27px;
				margin-right: 45px;
				user-select: none;
				color: red;
				animation: pulse 1.1s infinite;

				@keyframes pulse {
					0% {
						transform: scale(0.88);
						opacity: 0.8;
					}
					70% {
						transform: scale(1);
						opacity: 0.7;
					}
					100% {
						transform: scale(0.95);
						opacity: 0.7;
					}
				}

				&:hover {
					color: darkred;
					animation: none;
				}
			}

			a {
				margin-right: 34px;
				&:hover {
					color: gold;
				}
			}
		}
	}
}
</style>
