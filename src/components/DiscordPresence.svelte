<script lang="ts">
	import { onMount } from 'svelte';
	import io from 'socket.io-client';
	const socket = io('https://api.laith.app');

	const fetchPresence = async () => {
		const colors: { [key: string]: string } = {
			online: '#0ac14f',
			offline: '#dd0e34',
			idle: '#e08313',
			dnd: '#dd0e34'
		};

		socket.on('presence', (data) => {
			presence = data;
			hexColor = colors[presence.status];

			presence.color = {
				r: parseInt(hexColor.slice(1, 3), 16).toString(),
				g: parseInt(hexColor.slice(3, 5), 16).toString(),
				b: parseInt(hexColor.slice(5, 7), 16).toString()
			};

			setTimeout(() => {
				const dataBox = document.getElementById('data-box');
				if (dataBox) {
					dataBox.style.setProperty('--r', presence.color.r);
					dataBox.style.setProperty('--g', presence.color.g);
					dataBox.style.setProperty('--b', presence.color.b);
				}
			}, 200);
		});
	};

	let hexColor: string;

	let presence: {
		username: string;
		status: string;
		image: string;
		activity?: string;
		color: {
			r: string;
			g: string;
			b: string;
		};
	};

	onMount(async () => {
		await fetchPresence();
	});
</script>

{#if presence}
	<div id="main-div">
		<div id="data-box">
			<img src={presence.image} alt="my face lol" />
			<div id="text-box">
				<p id="username">{presence.username}</p>
				<p id="activity">
					{presence.activity !== 'null' ? presence.activity : "Sippin' the caffine..."}
				</p>
			</div>
		</div>
	</div>
{/if}

<style lang="scss">
	#main-div {
		height: 6rem;
		width: 40rem;

		display: flex;
		align-items: center;

		margin-inline: auto;
		margin-top: 100px;
		padding: 5px;
		align-items: center;

		#data-box {
			height: inherit;
			width: 26rem;

			border-radius: 1px 14px 1px 14px;

			display: flex;
			align-items: center;

			animation: slideIn 0.5s ease;
			animation-fill-mode: forwards;

			@keyframes slideIn {
				from {
					opacity: 0;
					transform: translateY(700px);
				}
				to {
					opacity: 1;
					transform: translateY(0);
				}
			}

			img {
				border-radius: 200px;
				height: 4.4rem;
				margin-left: 17px;
				z-index: 1000;
				border: 2px solid rgba(var(--r), var(--g), var(--b), 0.5);

				animation: pulse 1s infinite;

				@keyframes pulse {
					0% {
						box-shadow: 0 0 0 0 rgba(var(--r), var(--g), var(--b), 0.6);
						transform: scale(0.98);
					}
					70% {
						box-shadow: 0 0 0 6px rgba(var(--r), var(--g), var(--b), 0);
						transform: scale(1);
					}
					100% {
						box-shadow: 0 0 0 0 rgba(var(--r), var(--g), var(--b), 0);
						transform: scale(0.98);
					}
				}
			}

			#text-box {
				margin-inline: 12px;
				margin-top: 7px;

				display: flex;
				flex-direction: column;
				justify-content: space-around;

				height: 52px;

				animation: enter 0.5s ease;
				opacity: 0;
				animation-fill-mode: forwards;
				animation-delay: 0.5s;

				@keyframes enter {
					from {
						opacity: 0;
						transform: translateX( -90px); 
						color: $black;
					}
					to {
						opacity: 1;
						transform: translateX(0); /* Translate to original position */
					}
				}

				#username {
					font-size: 20px;
					font-weight: 600;
					letter-spacing: 1.6px;
				}

				#activity {
					font-size: 15px;
				}
			}
		}
	}
</style>
