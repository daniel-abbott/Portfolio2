<script>
    import { fade, fly } from 'svelte/transition';

    export let loadApp;
</script>

<style>
    .centered {
        font-size: 20vw;
        position: absolute;
        left: 50%;
        top: 50%;
        transform: translate(-50%, -50%);
        letter-spacing: 0.12em;
        color: black;
        font-weight: 100;
        text-align: center;
    }

    .centered span {
        will-change: filter;
    }
</style>

<div on:click={loadApp} class="centered" out:fly="{{y: -20, duration: 800}}">
    {#each 'DANIEL ABBOTT' as char, i}
        <span in:fade="{{delay: 1000 + i * 150, duration: 800}}">{char}</span>
    {/each}
</div>

