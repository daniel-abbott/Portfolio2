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
        color: var(--footer-text-color);
        /* background-color: white; */
    }
    span {
        font-size: 12px;
    }
</style>

<div in:fade="{{delay: 800, duration: 800}}">
    <span>(C) 2019 Daniel Abbott</span>
</div>