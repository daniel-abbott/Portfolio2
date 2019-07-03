<script>
    import Card from './Card.svelte';
    export let title;
    export let cardObject;

    const cardWidth = cardObject.width;
    const cards = cardObject.cards;
</script>

<style>
    div {
        background-color: white;
        width: 95%;
        margin-bottom: 1em;
    }
</style>

<div>
    <h1>{title}</h1>
    {#each cards as card}
        <Card image={card.image} title={card.title} description={card.description} />
    {/each}
</div>