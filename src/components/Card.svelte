<script>
    import { fade, fly } from 'svelte/transition';

    export let width = 100;
    export let height = 100;
    export let image;
    export let title;
    export let description;

    let hovered = false;
</script>

<style>
    @keyframes cardMouseEnter {
        from {
            flood-color: transparent
        }
        to {
            flood-color: aliceblue;
        }
    }
    @keyframes cardMouseLeave {
        from {
            flood-color: aliceblue;
        }
        to {
            flood-color: transparent;
        }
    }
    .card {
        position: relative;
        animation-name: cardMouseLeave;
        animation-duration: 0.5s;
        background-color: white;
        margin: 0.5em;
        width: var(--width);
        height: var(--height);
        /* border: 1px solid white; */
        /* border-radius: 0.8em; */
        overflow: hidden;
        /* transform: scale(1.0); */
    }
    .card:hover {
        animation-name: cardMouseEnter;
        animation-duration: 0.5s;
    }
    .card-text {
        position: absolute;
        bottom: 0;
        left: 0;
        padding-left: 0.5em;
        /* padding-right: 1em; */
        background-color: rgba(255, 255, 255, 1);
        width: 100%;
        /* box-shadow: 0px -1px 5px blue; */
    }
</style>

<div on:mouseleave="{() => hovered=false}" on:mouseenter="{() => hovered=true}" in:fade="{{ delay: 800, duration: 800 }}" class="card" style="--width: {width}; --height: {height};">
    {#if image}
        <img src={image} alt="placeholder" width="100%" height="100%"/>
    {/if}
    {#if hovered || !image}
    <div transition:fly="{{ y:100, duration: 600 }}" class="card-text">
        <h3 transition:fly="{{ y:100, duration: 800 }}">{title}</h3>
        <p transition:fly="{{ y:100, duration: 1000 }}">{description}</p>
    </div>
    {/if}
</div>
