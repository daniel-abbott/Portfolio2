<script>
    import { fly } from 'svelte/transition';

    export let stateChangeDuration;
    export let title;
    export let textObject;
    export let id;
    export let about = false;
</script>

<style>
    .textblock {
        display: flex;
        flex-flow: column wrap;
        position: absolute;
        top: 0;
        width: 95%;
        /* margin-bottom: 1em; */
        border-radius: var(--standard-radius);
        z-index: 1;
        overflow: hidden;
    }
    .textblock-title {
        background-color: var(--main-header-color);
        padding: 0.5em;
        color: var(--main-title-color);
    }
    .textblock-text {
        padding-left: 1em;
        background-color: var(--main-body-color);
        color: var(--main-text-color);
    }
    h1 {
        margin: 0;
    }
    p {
        /* margin: 0; */
        /* background-color: rgb(58, 58, 129); */
    }
    .hero-image {
        /* animation: imageScroll 4s linear infinite; */
        width: 100%;
        height: 500px;
        background-image: var(--background-image);
        background-repeat: repeat-x;
        background-size: cover;
        background-position: 0px 0px;
    }
    @keyframes imageScroll {
        from {
            background-position: 0 0;
        }
        to {
            background-position: 100% 0;
        }
    }
</style>

<section transition:fly="{{ y: 1000, duration: stateChangeDuration }}" id={id} class="textblock">
    <div class="textblock-title">
        <h1>{title}</h1>
    </div>
    {#if textObject.image}
        <div class="hero-image" style="--background-image: url({textObject.image});" alt="placeholder" />
        {#if about}
            <p>PPPPPP</p>
        {/if}
    {/if}
    <div class="textblock-text">
        <p>{@html textObject.text}</p>
    </div>
</section>