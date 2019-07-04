<script>
    import TextBlock from './TextBlock.svelte';
    import CardList from './CardList.svelte';

    import projects from '../data/projects.js';
    import blog from '../data/blog.js';
    import contributions from '../data/contributions.js';
</script>

<style>
    div {
        display: flex;
        flex-flow: column nowrap;
        align-items: center;
    }
</style>

<div>
    <TextBlock title="About" />
    <CardList title="Projects" cardObject={projects} />
    <CardList title="Blog" cardObject={blog} />
    <CardList title="Contributions" cardObject={contributions} />
    <TextBlock title="Contact" />
</div>