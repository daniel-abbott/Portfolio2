<script>
    import { fade, fly } from 'svelte/transition';
    import { getContext } from 'svelte';

    export let width = 100;
    export let height = 100;
    export let data;

    const activateModal = getContext('activateModal');

    let hovered = false;
</script>

<style>
    @keyframes cardMouseEnter {
        from {
            transform: scale(1.0);
        }
        to {
            transform: scale(1.1);
        }
    }
    @keyframes cardMouseLeave {
        from {
            transform: scale(1.1);
        }
        to {
            transform: scale(1.0);
        }
    }
    .card {
        position: relative;
        /* animation-name: cardMouseLeave;
        animation-duration: 0.5s; */
        background-color: var(--secondary-body-color);
        margin: 0.5em;
        width: var(--width);
        height: var(--height);
        /* border: 1px solid white; */
        border-radius: var(--standard-radius);
        overflow: hidden;
        box-shadow: 0;
        cursor: pointer;
    }
    .card:hover {
        box-shadow: var(--shadow);
    }
    .card:active {
        transform: scale(0.99);
    }
    .card-text {
        background-color: inherit;
        position: absolute;
        bottom: 0;
        left: 0;
        padding-left: 0.5em;
        /* padding-right: 1em; */
        width: 100%;
        /* box-shadow: 0px -1px 5px blue; */
        color: var(--secondary-text-color);
        pointer-events: none;
    }
    img:hover {
        animation-name: cardMouseEnter;
        animation-duration: 2s;
        transform: scale(1.1);
    }
</style>

<div on:click="{() => activateModal(data)}" on:mouseleave="{() => hovered=false}" on:mouseenter="{() => hovered=true}" in:fade="{{ delay: 800, duration: 800 }}" class="card" style="--width: {width}; --height: {height};">
    {#if data.image}
        <img src={data.image} alt="placeholder" width="100%" height="100%"/>
    {/if}
    {#if hovered || !data.image}
    <div transition:fly="{{ y:100, duration: 600 }}" class="card-text">
        <h3 transition:fly="{{ y:100, duration: 800 }}">{data.title}</h3>
        <p transition:fly="{{ y:100, duration: 1000 }}">{data.description}</p>
    </div>
    {/if}
</div>
