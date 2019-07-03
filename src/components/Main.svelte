<script>
    import TextBlock from './TextBlock.svelte';
    import CardList from './CardList.svelte';

    const projects = {
        width: "25%",
        cards: [
            {
                image: "Placeholder 1",
                title: "Test 1",
                description: "Test text 1"
            },
            {
                image: "Placeholder 2",
                title: "Test 2",
                description: "Test text 2"
            },
        ]
    };
</script>

<style>
    div {
        display: flex;
        flex-flow: column nowrap;
        align-items: center;
        width: 95%;
    }
</style>

<div>
    <TextBlock title="About" />
    <CardList title="Projects" cardObject={projects}/>
    <!-- <CardList title="Blog" /> -->
    <!-- <CardList title="Contributions" /> -->
    <TextBlock title="Contact" />
</div>