<script>
    import TextBlock from './TextBlock.svelte';
    import CardList from './CardList.svelte';
    import projects from '../data/projects.js';
    import blog from '../data/blog.js';
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
    <CardList title="Projects" cardObject={projects} />
    <CardList title="Blog" cardObject={blog} />
    <!-- <CardList title="Contributions" /> -->
    <TextBlock title="Contact" />
</div>