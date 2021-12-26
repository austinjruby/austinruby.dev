<script>
	import { onMount } from 'svelte';
	import Descriptor from './Descriptor.svelte';

	let activeIndex = 0;

	// TODO add links to some of these
	// TODO add clickme tooltip
	const descriptors = [
		'Software engineer @ Medly',
		'Scrambling golfer',
		'Ex-bartender',
		'Opinionated bagel lover',
		'Used book reader',
		'Ex-Tesla',
		'Dog parent',
		'Soul revival listener',
		'Ex-pastrami hawker',
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
		{#each descriptors as descriptor, index}
			<Descriptor text={descriptor} visible={index === activeIndex} />
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