<script>
    import { fade } from 'svelte/transition';

    export let text;
    export let visible;
    export let link;

    const fadeConfig = { duration: 700 };
</script>

{#if visible}
    {#if link}
        <a href={link} target='none' in:fade={fadeConfig}>{text}</a>
    {:else}
        <p in:fade={fadeConfig}>{text}</p>
    {/if}
{/if}

<style>
    p, a {
		color: #E0CEF3;
		font-size: 2vw;
		margin: 0;
        font-family: 'Nunito Sans', sans-serif;
        text-decoration: none;
        transition: transform .2s, color .2s ease;
        padding: 0 2rem;
	}

    @media(hover: hover) {
        a:hover {
            color: #C19CE7;
            transform: scale(1.25);
        }
    }

    @media(max-width: 768px) {
        p {
            font-size: 4.5vw;
        }
    }
</style>