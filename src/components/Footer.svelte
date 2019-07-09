<script>
    import { fade } from 'svelte/transition';
</script>

<style>
    div {
        position: fixed;
        bottom: 0;
        display: flex;
        flex-flow: row nowrap;
        flex-direction: row-reverse;
        width: 100%;
        z-index: 1;
        /* background-color: white; */
    }
</style>

<div in:fade="{{delay: 800, duration: 800}}">
    (C) 2019 Daniel Abbott
</div>