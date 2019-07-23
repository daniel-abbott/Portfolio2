<script>
    import { fly } from 'svelte/transition';

    export let appStates;
    export let currentState;
    export let changeState;
</script>

<style>
    nav {
        position: -webkit-sticky;
        position: sticky;
        top: 0;
        display: flex;
        flex-flow: row nowrap;
        justify-content: space-between;
        align-items: center;
        background-color: var(--nav-color);
        width: 100%;
        box-shadow: var(--shadow);
        z-index: 100;
    }
    h3 {
        padding-left: 2em;
    }
    ul {
        display: flex;
        padding-right: 2em;
    }
    span {
        margin-left: 1em;
        color: var(--nav-text-color);
        transition: color 0.2s ease-out;
        text-decoration: none;
        cursor: pointer;
        font-weight: normal;
    }
    span:hover {
        color: var(--nav-highlight-color);
    }
    span:active {
        color: var(--nav-click-color);
    }
</style>

<nav in:fly="{{y: -100, duration: 1000}}">
    <h3>Daniel Abbott</h3>
    <ul bind>
        <span on:click="{() => changeState(0)}">About</span>
        <span on:click="{() => changeState(1)}">Projects</span>
        <span on:click="{() => changeState(2)}">Blog</span>
        <span on:click="{() => changeState(3)}">Contributions</span>
        <span on:click="{() => changeState(4)}">Contact</span>
    </ul>
</nav>
