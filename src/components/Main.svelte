<script>
    import TextBlock from './TextBlock.svelte';
    import CardList from './CardList.svelte';
    import { fly } from 'svelte/transition';

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

<div in:fly="{{y: 100, delay: 800, duration: 800}}">
    <TextBlock id="about" title="About" />
    <CardList id="projects" title="Projects" cardObject={projects} />
    <CardList id="blog" title="Blog" cardObject={blog} />
    <CardList id="contrib" title="Contributions" cardObject={contributions} />
    <TextBlock id="contact" title="Contact" />
</div>