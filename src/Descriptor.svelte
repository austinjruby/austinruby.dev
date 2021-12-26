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
		font-size: 2vw;
		margin: 0;
        font-family: 'Nunito Sans', sans-serif;
	}

    @media(max-width: 768px) {
        p {
            font-size: 4.5vw;
        }
    }
</style>