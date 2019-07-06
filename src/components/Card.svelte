<script>
    import { fade } from 'svelte/transition';

    export let width = 100;
    export let height = 100;
    export let image;
    export let title;
    export let description;
</script>

<style>
    .card {
        perspective: 1000px;
        margin: 0.5em;
    }
        .card:hover .flip-card, .card.hover .flip-card {
            transform: rotateY(180deg);
        }
    .card, .front, .back {
        width: var(--width);
        height: var(--height);
    }
    .flip-card {
        transition: 0.6s;
        transform-style: preserve-3d;
        position: relative;
    }
    .front, .back {
        /* box-shadow: 2px 2px 2px black; */
        backface-visibility: hidden;
        border: 1px solid gray;
        border-radius: 0.3em;
        position: absolute;
        top: 0;
        left: 0;
    }
    .front {
        background-color: white;
        z-index: 2;
        transform: rotateY(0deg);
    }
    .back {
        background-color: lightgray;
        transform: rotateY(180deg);
    }
    .card-text {
        padding-left: 0.2em;
        padding-right: 0.2em;
    }
    img {
        border-top-left-radius: 0.3em;
        border-top-right-radius: 0.3em;
    }
</style>

<div in:fade="{{delay: 1200, duration: 800}}" class="card" style="--width: {width}; --height: {height};" ontouchstart="this.classList.toggle('hover');">
    <div class="flip-card">
        <div class="front">
            {#if image}
                <img src={image} alt="placeholder" width="100%" />
            {/if}
            <div class="card-text">
                <h3>{title}</h3>
                <p>{description}</p>
            </div>
        </div>
        <div class="back">
            Test!
        </div>
    </div>
</div>
