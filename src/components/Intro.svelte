<script>
    import { fade, fly } from 'svelte/transition';

    export let loadApp;
    let name = 'DANIEL ABBOTT';
    let counter = 0;

    const countUp = () => {
        counter++;

        if (counter === name.length) {
            counter = 0;
            setTimeout(loadApp, 800);
        }
    }
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

<div class="centered" out:fly="{{y: -20, duration: 800}}">
    {#each name as char, i}
        <span on:introend="{() => countUp()}" in:fade="{{delay: 1000 + i * 300, duration: 1000}}">{char}</span>
    {/each}
</div>