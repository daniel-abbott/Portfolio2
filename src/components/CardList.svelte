<script>
    import Card from './Card.svelte';
    import { fly } from 'svelte/transition';

    export let title;
    export let cardObject;
    export let id;
    export let stateChangeDuration;

    const cardWidth = cardObject.width;
    const cardHeight = cardObject.height;
    const cards = cardObject.cards;
</script>

<style>
    .cardList {
        position: absolute;
        top: 0;
        display: flex;
        flex-flow: column nowrap;
        color: white;
        width: 95%;
        max-height: 90%;
        /* height: 100%; */
        /* margin-bottom: 1em; */
        border-radius: var(--standard-radius);
        z-index: 1;
        overflow: hidden;
    }
    .cardList-title {
        background-color: var(--main-header-color);
        padding: 0.5em;
        color: var(--main-title-color);
    }
    .cardList-cards {
        background-color: var(--main-body-color);
        display: flex;
        flex-flow: row wrap;
        justify-content: space-between;
        padding: 0.5em;
        color: var(--main-text-color);
        overflow: auto;
    }
    h1 {
        margin: 0;
    }
</style>

<section transition:fly="{{ y: 1000, duration: stateChangeDuration }}" id={id} class="cardList">
    <div class="cardList-title">
        <h1>{title}</h1>
    </div>
    <div class="cardList-cards">
        {#each cards as card, i}
            <Card width={cardWidth} height={cardHeight} data={card} />
        {/each}
    </div>
</section>
