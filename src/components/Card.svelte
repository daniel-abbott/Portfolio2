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
    @keyframes scaleCardOut {
        from {
            transform: scale(1.0);
        }
        to {
            transform: scale(1.01);
        }
    }
    @keyframes scaleCardIn {
        from {
            transform: scale(1.01);
        }
        to {
            transform: scale(1.0);
        }
    }
    .card {
        animation-name: scaleCardIn;
        animation-duration: 0.5s;
        background-color: white;
        margin: 0.5em;
        width: var(--width);
        height: var(--height);
        border: 1px solid black;
        border-radius: 0.3em;
        transform: scale(1.0);
        overflow: hidden;
    }
    .card:hover {
        animation-name: scaleCardOut;
        animation-duration: 0.5s;
        transform: scale(1.01);
    }
    .card-text {
        position: absolute;
        bottom: 0;
        left: 0;
        padding-left: 0.2em;
        padding-right: 0.2em;
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
