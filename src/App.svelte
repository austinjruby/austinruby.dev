<script>
	import { onMount } from 'svelte';
	import Descriptor from './Descriptor.svelte';

	let activeIndex = 0;

	const descriptors = [
		{ text: 'Software engineer @ Medly', link: 'https://medly.com/en-us' },
		{ text: 'Delusional golfer', link: 'https://www.youtube.com/watch?v=zbQTXFJL8lo&ab_channel=MiGustaTacoBell' },
		{ text: 'Ex-bartender', link: 'https://www.instagram.com/2ndfloorbaressen/' },
		{ text: 'Opinionated bagel lover', link: 'http://ourbksocial.com/searching-brooklyns-bodacious-bagel-conclusion/' },
		{ text: 'Used book reader', link: 'https://www.thriftbooks.com/w/post-office_charles-bukowski/265076/?resultid=37acd627-02cd-4745-96de-93ef48d06427#edition=14624442&idiq=46472774' },
		{ text: 'Ex-Tesla', link: 'https://twitter.com/elonmusk?ref_src=twsrc%5Egoogle%7Ctwcamp%5Eserp%7Ctwgr%5Eauthor' },
		{ text: 'Dog parent', link: '/cora.jpg' },
		{ text: 'Soul revival listener', link: 'https://open.spotify.com/track/7APxY3crOzJpHfIwH57DcH?si=b34dfec57e164258' },
		{ text: 'Ex-pastrami hawker', link: 'https://2ndavedeli.com/' },
	];

	onMount(() => {
		const rotateSpeed = 2500;
		const rotator = setInterval(() => {
			if (activeIndex === descriptors.length - 1) {
				activeIndex = 0;
			} else {
				activeIndex += 1;
			}
		}, rotateSpeed);

		return () => clearInterval(rotator);
	})
</script>

<main>
	<div id="header-container">
		<h1>Austin Ruby</h1>
		{#each descriptors as { text, link }, index}
			<Descriptor {text} {link} visible={index === activeIndex} />
		{/each}
	</div>
</main>

<style>
	@import url('https://fonts.googleapis.com/css2?family=Lato&family=Marcellus&family=Nunito+Sans:wght@300&display=swap');

	main {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		width: 100%;
		height: 100%;
	}

	#header-container {
		width: 100%;
		display: flex;
		flex-direction: column;
		align-items: center;
	}

	h1 {
		color: #FFFDE7;
		font-family: 'Marcellus', serif;
		font-size: 11.1vw;
		font-weight: 100;
		margin: 0 0 1rem 0;
	}

	@media(max-width: 768px) {
		h1 {
			font-size: 22.2vw;
			text-align: center;
		}
	}
</style>