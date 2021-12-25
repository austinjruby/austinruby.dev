<script>
    import { fade } from 'svelte/transition';

    export let text;
    export let visible;
</script>

{#if visible}
    <p in:fade={{ duration: 700 }}>{text}</p>
{/if}

<style>
    p {
		color: #E0CEF3;
		font-size: 1.7rem;
		margin: 0;
        font-family: 'Nunito Sans', sans-serif;
	}
</style>