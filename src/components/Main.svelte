<script>
    import TextBlock from './TextBlock.svelte';
    import CardList from './CardList.svelte';
    import { fly } from 'svelte/transition';

    import about from '../data/about.js';
    import projects from '../data/projects.js';
    import blog from '../data/blog.js';
    import contributions from '../data/contributions.js';

    export let appStates;
    export let currentState;
    export let stateChangeDuration;
</script>

<style>
    main {
        background: transparent;
        margin-top: 2vh;
        position: relative;
        display: flex;
        flex-flow: column nowrap;
        align-items: center;
        width: 100%;
        height: 100%;
        overflow: hidden;
    }
</style>

<main transition:fly="{{ y: 100, delay: 800, duration: 800 }}">
    {#if currentState === appStates.ABOUT}
        <TextBlock about="true" {stateChangeDuration} id="about" title="About" textObject={about} />
    {:else if currentState === appStates.PROJECTS}
        <CardList {stateChangeDuration} id="projects" title="Projects" cardObject={projects} />
    {:else if currentState === appStates.BLOG}
        <CardList {stateChangeDuration} id="blog" title="Blog" cardObject={blog} />
    {:else if currentState === appStates.CONTRIB}
        <CardList {stateChangeDuration} id="contrib" title="Contributions" cardObject={contributions} />
    {:else if currentState === appStates.CONTACT}
        <TextBlock {stateChangeDuration} id="contact" title="Contact" />
    {/if}
</main>