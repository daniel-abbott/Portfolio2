<script>
    import { fly } from 'svelte/transition';

    export let stateChangeDuration;
    export let title;
    export let id;
</script>

<style>
    .textblock {
        position: absolute;
        top: 0;
        background-color: white;
        width: 95%;
        margin-bottom: 1em;
        border-radius: 0.3em;
        z-index: 1;
    }
    .textblock-text {
        padding-left: 0.5em;
    }
</style>

<section transition:fly="{{ y: 1000, duration: stateChangeDuration }}" id={id} class="textblock">
    <div class="textblock-text">
        <h1>{title}</h1>
        <p>Words</p>
    </div>
</section>