<script lang="ts">
	import DiscordPresence from '../components/DiscordPresence.svelte';
	import Header from '../components/Header.svelte';
	const aboutMeStrr =
		'Hello, my name is Laith Al Nabulsi im a 17 year old junior software developer. I was born on October 9 2005 and died on... nvm i am still alive (thankfully).';
</script>

<Header />
<div id="main-div">
	<p id="name">Laith Nabulsi</p>
	<p id="about-me">{@html aboutMeStrr}</p>
	<p id="quote">┃#1 Sleep Addict</p>
</div>
<DiscordPresence />

<style lang="scss">
	#main-div {
		height: 4rem;
		width: 40rem;
		display: flex;
		flex-direction: column;
		margin-inline: auto;
		padding: 5px;

		#name {
			font-size: 25px;
			font-weight: 600;
			font-family: 'Ubuntu';
			letter-spacing: 3px;
			margin-bottom: 20px;
		}

		#quote {
			letter-spacing: 3px;
			margin-top: 20px;
			color: orange;
		}
	}
</style>
