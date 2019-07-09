<script>
    import TextBlock from './TextBlock.svelte';
    import CardList from './CardList.svelte';
    import { fly } from 'svelte/transition';

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
        z-index: 1;
    }
    main:after {
        background:orange;
        bottom: 0;
        content: '';
        display: block;
        height: 20%;
        left: 0;
        position: absolute;
        right: 0;
        transform: skewY(-4.8deg);
        transform-origin: 100%;
        z-index: -1;
    }
</style>

<main transition:fly="{{y: 100, delay: 800, duration: 800}}">
    {#if currentState === appStates.ABOUT}
        <TextBlock stateChangeDuration={stateChangeDuration} id="about" title="About" />
    {:else if currentState === appStates.PROJECTS}
        <CardList stateChangeDuration={stateChangeDuration} id="projects" title="Projects" cardObject={projects} />
    {:else if currentState === appStates.BLOG}
        <CardList stateChangeDuration={stateChangeDuration} id="blog" title="Blog" cardObject={blog} />
    {:else if currentState === appStates.CONTRIB}
        <CardList stateChangeDuration={stateChangeDuration} id="contrib" title="Contributions" cardObject={contributions} />
    {:else if currentState === appStates.CONTACT}
        <TextBlock stateChangeDuration={stateChangeDuration} id="contact" title="Contact" />
    {/if}
</main>