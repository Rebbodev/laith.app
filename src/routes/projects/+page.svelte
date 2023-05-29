<script lang="ts">
	import { onMount } from 'svelte';
	import Header from '../../components/Header.svelte';
	import errorpng from '../../images/error.png';

	const projects: {
		image: string;
		title: string;
		description: string;
		link: string;
		projectId: string;
	}[] = [
		
	];

	let animated = false;

	onMount(() => {
		animated = true;
	});
</script>

<Header />

{#if projects.length > 0}
	<div id="main-div">
		{#each projects as project, index}
			<a href={project.link}>
				<div id="project-box" class:animate={animated} style="animation-delay: {index * 0.1}s">
					<div id="box-elem">
						<img src={project.image} alt={project.title.toLowerCase()} />
						<div id="text">
							<p>{project.title}</p>
							<p id="desc">{project.description}</p>
						</div>
					</div>
				</div>
			</a>
		{/each}
	</div>
{:else if projects.length === 0}
	<div id="main-div">
		<a href="/projects">
			<div id="project-box" class:animate={animated} style="animation-delay: {1 * 0.1}s">
				<div id="box-elem">
					<img src={errorpng} alt="error.png" />
					<div id="text">
						<p>{'No Projects'}</p>
						<p id="desc">
							{'Projects have yet to be added to the website check back in july. XoXo <3'}
						</p>
					</div>
				</div>
			</div>
		</a>
	</div>
{/if}

<style lang="scss">
	#main-div {
		height: auto;
		width: 40rem;
		margin-inline: auto;
		display: flex;
		flex-direction: column;

		#project-box {
			width: auto;
			height: auto;
			display: flex;
			align-items: center;
			background-color: rgb(56, 56, 56);
			border-radius: 7px;
			padding: 14px;
			margin-bottom: 15px;
			opacity: 0;

			animation: slideIn 0.5s ease;
			animation-fill-mode: forwards;

			@keyframes slideIn {
				from {
					opacity: 0;
					transform: translateX(700px);
				}
				to {
					opacity: 1;
					transform: translateX(0);
				}
			}

			animation: slideIn 0.5s ease;
			animation-fill-mode: forwards;

			@keyframes slideIn {
				from {
					opacity: 0;
					transform: translateX(700px);
				}
				to {
					opacity: 1;
					transform: translateX(0);
				}
			}

			.animate {
    animation-delay: 0.5s; /* Delay the initial animation */
  }

			&:hover {
				background-color: rgba(75, 75, 75, 0.418);
			}

			#box-elem {
				display: flex;

				img {
					height: 100px;
					border-radius: 3px;
					margin-right: 18px;
				}
				#text {
					display: flex;
					flex-direction: column;
					align-self: flex-start;
					margin-top: 10px;
					p {
						align-self: flex-start;
						font-family: 'Poppins';
						font-weight: 600;
						font-size: 1.3rem;
					}
					#desc {
						font-weight: 100;
						font-size: 13px;
					}
				}
			}
		}
	}
</style>
