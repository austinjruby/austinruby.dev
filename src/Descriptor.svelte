<script>
    import { fade } from 'svelte/transition';

    export let text;
    export let visible;
    export let link;

    const fadeConfig = { duration: 700 };

    const textColor = '#E0CEF3';
    const textColorHover = '#C19CE7'
</script>

{#if visible}
    {#if link}
        <a
            href={link}
            target='none'
            in:fade={fadeConfig}
            style='--text-color: {textColor}; --text-color-hover: {textColorHover};'
        >
            {text}
        </a>
    {:else}
        <p style='--text-color: {textColor};' in:fade={fadeConfig}>{text}</p>
    {/if}
{/if}

<style>
    p, a {
		color: var(--text-color);
		font-size: 2vw;
		margin: 0;
        font-family: 'Nunito Sans', sans-serif;
        padding: 0 2rem;
	}

    a {
        position: relative;
        text-decoration: none;
        transition: transform .2s, color .2s ease;
    }

    @media(hover: hover) {
        a::before {
            content: "";
            position: absolute;
            display: block;
            width: calc(100% - 4rem);
            height: .15vw;
            bottom: 0;
            left: 2rem;
            background-color: var(--text-color);
            transform: scaleX(0);
            transition: transform 0.2s ease;
        }
        
        a:hover {
            color: var(--text-color-hover);
            transform: scale(1.1);
        }

        a:hover::before {
            background-color: var(--text-color-hover);
            transform: scaleX(1);
        }
    }

    @media(max-width: 768px) {
        p, a {
            font-size: 4.5vw;
        }
    }
</style>