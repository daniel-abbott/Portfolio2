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
        background-color: white;
        width: 95%;
        /* margin-bottom: 1em; */
        border-radius: 0.3em;
        z-index: 1;
    }
    .cardList-title {
        padding-left: 0.5em;
    }
    .cardList-cards {
        display: flex;
        flex-flow: row wrap;
        justify-content: space-between;
        padding: 0.5em;
    }
</style>

<section transition:fly="{{ y: 1000, duration: stateChangeDuration }}" id={id} class="cardList">
    <div class="cardList-title">
        <h1>{title}</h1>
    </div>
    <div class="cardList-cards">
        {#each cards as card, i}
            <Card width={cardWidth} height={cardHeight} image={card.image} title={card.title} description={card.description} />
        {/each}
    </div>
</section>
