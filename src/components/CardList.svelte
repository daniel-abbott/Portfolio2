<script>
    import Card from './Card.svelte';
    export let title;
    export let cardObject;

    const cardWidth = cardObject.width;
    const cards = cardObject.cards;
</script>

<style>
    .cardList {
        display: flex;
        flex-flow: column nowrap;
        background-color: white;
        width: 95%;
        margin-bottom: 1em;
        border-radius: 0.3em;
    }
    .cardList-title {
        padding-left: 0.5em;
    }
    .cardList-cards {
        display: flex;
        flex-flow: row wrap;
    }
</style>

<div class="cardList">
    <div class="cardList-title">
        <h1>{title}</h1>
    </div>
    <div class="cardList-cards">
        {#each cards as card}
            <Card width={cardWidth} image={card.image} title={card.title} description={card.description} />
        {/each}
    </div>
</div>
